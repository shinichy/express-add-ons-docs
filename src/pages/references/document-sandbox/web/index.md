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
title: Web APIs
description: An overview of the Web APIs available as part of the document sandbox.
contributors:
  - https://github.com/hollyschinsky
---

# Web APIs

The Web APIs refer to the set of commonly used APIs that are injected by the script runtime into the global context to allow you to access common JavaScript functions.

## Overview

The Web APIs provide implementations of some common objects and functions for you to use in your script code to perform things like logging to the console. They are limited to a set of basic functions currently, as outlined in the next section. Most of the browsers APIs/Global Objects are not available in Script Runtime. For these, the developers can use iframe runtime environment and [communicate](../communication/index.md#expose-apis-from-the-ui) the result back to the script running inside script runtime environment.

<InlineAlert slots="text" variant="success"/>

These APIs can automatically be used in your script runtime code.

## Console Object

A global [`console`](https://developer.mozilla.org/en-US/docs/Web/API/console) object implementation is provided with the following JavaScript method implementations for use in your script code.

### console.log()

For general output of logging information. You may use string substitution and additional arguments with this method.

### console.info()

Informative logging of information. You may use string substitution and additional arguments with this method.

### console.warn()

Outputs a warning message. You may use string substitution and additional arguments with this method.

### console.error()

Outputs an error message. You may use string substitution and additional arguments with this method.

### console.debug()

Outputs a message to the console with the log level debug.

### console.clear()

Clear the console.

### console.assert()

Log a message and stack trace to console if the first argument is false.
