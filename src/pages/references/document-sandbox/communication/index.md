---
keywords:
  - Adobe Express
  - Express Add-on SDK
  - Express Editor
  - Adobe Express
  - Add-on SDK
  - SDK
  - JavaScript
  - Extend
  - Extensibility
  - API
  - Add-on Manifest
title: Communication APIs
description: An introduction to the Communication APIs available in the document sandbox.
contributors:
  - https://github.com/hollyschinsky  
hideBreadcrumbNav: true
---

# Communication APIs

The communication APIs allow you to communicate between the document model sandbox (referred to as simply "document sandbox" throughout the rest of this guide), and the iframe where your add-on is running specifically via the add-on SDK methods available for the document sandbox.

## Overview

The document sandbox and iframe runtime are two different runtime execution environments which are present on different threads in the browser. The communication APIs are based on the [Comlink library](https://github.com/GoogleChromeLabs/comlink) and provide a mechanism to allow the JavaScript code executing in each to interact. Developers can call the apis exposed in one environment (ie: document sandbox) from another environment (ie: iframe where their add-on is running) bidirectionally.

## Accessing the APIs

A default exported module from `AddOnScriptSdk` is provided to enable the communication between the iframe and the document sandbox via its' `instance.runtime` object. You can simply import the module into your script file code for use, and create a reference to the `runtime` object. For instance:

```js
// import addOnSandboxSdk from "add-on-sdk-document-sandbox" - TODOHS
import AddOnScriptSdk from "AddOnScriptSdk"; // AddOnScriptSdk is a default import

const { runtime } = AddOnScriptSdk.instance; // runtime object provides direct access to the comm methods
```

## Examples

The `runtime` object can then be used to access the communication methods which allow you to communicate between the two execution environments: `exposeApi()` and `apiProxy()`. The examples below show the methods in use from both the `index.html` where the iframe is running with your add-on code, and the document sandbox environment running the contents of `code.js`.

### Expose APIs from the script

This example shows how to expose APIs from the document sandbox SDK (via `code.js`) for use by the UI (via `index.html`).

#### `code.js`

```js
// import addOnSandboxSdk from "add-on-sdk-document-sandbox" - TODOHS
import AddOnScriptSdk from "AddOnScriptSdk"; 

const { runtime } = AddOnScriptSdk.instance; 

const scriptApis = {
    performWorkOnDocument: function (data, someFlag) {
        // call the Document APIs
    },
    getDataFromDocument: function () {
        // get some data from document
    },
};
// expose these apis to be directly consumed in the UI (ie: index.html file).
runtime.exposeApi(scriptApis);
```

#### index.html

```js
import addOnUISdk from "https://new.express.adobe.com/static/add-on-sdk/sdk.js";

addOnUISdk.ready.then(async () => {
    const { runtime } = addOnUISdk.instance;

    // Wait for the promise to resolve to get a proxy to call APIs defined in the script
    const scriptApis = await runtime.apiProxy("script");

    await scriptApis.performWorkOnDocument(
        {
            pageNumber: 1,
            op: "change_background_color",
            data: {
                toColor: "blue",
            },
        }, 
        true
    );

    console.log(await scriptApis.getDataFromDocument());
});
```

### Expose APIs from the UI

This example shows how to expose APIs from the UI (via `index.html`) for use in the document sandbox (via `code.js`).

#### `index.html`

```js
addOnUISdk.ready.then(async () => {
    console.log("addOnUISdk is ready for use.");

    const { runtime } = addOnUISdk.instance;
    const uiApi = {
        performWorkOnUI: function (data, someFlag) {
            // Do some ui operation
        },
        getDataFromUI: async function () {            
            const promise = new Promise((resolve) => {
                resolve("button_color_blue");
            });

            return await promise;
        },
    };
    // Expose the UI Apis to be used in the script code (ie: code.js)
    runtime.exposeApi(uiApi);
});
```

#### `code.js`

```js
// import addOnSandboxSdk from "add-on-sdk-document-sandbox" - TODOHS
import AddOnScriptSdk from "AddOnScriptSdk"; // default import

const { runtime } = AddOnScriptSdk.instance;

async function callUIApis() {
    // Get a proxy to the APIs defined in the UI
    const uiApis = await runtime.apiProxy("panel");
    await uiApis.performWorkOnUI(
        {
            buttonTextFont: 20,
            buttonColor: "Green"
        },
        true
    );

    const result = await uiApis.getDataFromUI();
    console.log("Data from UI: " + result);
}
```

<InlineAlert slots="text" variant="info"/>

**DEBUGGING:** Since the script code runs in a separate context from your add-on UI, the only support for debugging is via the `console.*` methods.
