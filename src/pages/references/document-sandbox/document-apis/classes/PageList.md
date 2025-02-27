[@express-document-sdk](../overview.md) / PageList

# Class: PageList

PageList represents an ordered list of PageNodes, all of which are children of the root node of the document's "scenegraph"
artwork tree. A page contains one or more artboards, representing "scenes" in a linear timeline sequence. Those artboards
in turn contain all the visual content of the document.

PageList also provides APIs for adding/removing pages from the document. PageList is never empty: it is illegal to
remove the last remaining page from the list.

## Hierarchy

- [`RestrictedItemList`](RestrictedItemList.md)<[`PageNode`](PageNode.md)\>

  ↳ **`PageList`**

## Table of contents

### Accessors

- [first](PageList.md#first)
- [last](PageList.md#last)
- [length](PageList.md#length)

### Methods

- [[iterator]](PageList.md#iterator)
- [addPage](PageList.md#addpage)
- [indexOf](PageList.md#indexof)
- [item](PageList.md#item)
- [moveAfter](PageList.md#moveafter)
- [moveBefore](PageList.md#movebefore)
- [remove](PageList.md#remove)
- [toArray](PageList.md#toarray)

## Accessors

### first

• `get` **first**(): `undefined` \| `T`

First item in this list, or undefined if list is empty.

#### Returns

`undefined` \| `T`

#### Inherited from

RestrictedItemList.first

___

### last

• `get` **last**(): `undefined` \| `T`

Last item in this list, or undefined if list is empty.

#### Returns

`undefined` \| `T`

#### Inherited from

RestrictedItemList.last

___

### length

• `get` **length**(): `number`

Number of items in this list.

#### Returns

`number`

#### Inherited from

RestrictedItemList.length

## Methods

### [iterator]

▸ **[iterator]**(): `Iterator`<[`PageNode`](PageNode.md), `any`, `undefined`\>

Iterates over all the items in this list. Mutations that occur mid-iteration are not reflected by the iterator.

#### Returns

`Iterator`<[`PageNode`](PageNode.md), `any`, `undefined`\>

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[[iterator]](RestrictedItemList.md#iterator)

___

### addPage

▸ **addPage**(`geometry`): [`PageNode`](PageNode.md)

Create a new page containing a single empty artboard, and add it to the end of the list. The artboard is configured
with the same defaults as in [addArtboard](ArtboardList.md#addartboard). The page's artboard becomes the default target for
newly inserted content ([insertionParent](Context.md#insertionparent)) and the viewport switches to display this artboard.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `geometry` | [`RectangleGeometry`](../interfaces/RectangleGeometry.md) | The size of the new page. |

#### Returns

[`PageNode`](PageNode.md)

___

### indexOf

▸ **indexOf**(`item`): `number`

Get index of item in list.

#### Parameters

| Name | Type |
| :------ | :------ |
| `item` | [`PageNode`](PageNode.md) |

#### Returns

`number`

index number, or -1 if item isn't in this list.

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[indexOf](RestrictedItemList.md#indexof)

___

### item

▸ **item**(`index`): `undefined` \| [`PageNode`](PageNode.md)

Returns item at the given index, or undefined if index is out of range.

#### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `index` | `number` | Zero-based index |

#### Returns

`undefined` \| [`PageNode`](PageNode.md)

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[item](RestrictedItemList.md#item)

___

### moveAfter

▸ **moveAfter**(`item`, `after`): `void`

Move `item` so it is immediately after `after` in this list: places `item` at the index one higher than `after`.
Depending on the position in the list `item` originally occupied, some other items in the list may shift to higher
or lower indices as a result. No-op if both arguments are the same item.

**`Throws`**

An error if either argument is not contained in this list.

#### Parameters

| Name | Type |
| :------ | :------ |
| `item` | [`PageNode`](PageNode.md) |
| `after` | [`PageNode`](PageNode.md) |

#### Returns

`void`

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[moveAfter](RestrictedItemList.md#moveafter)

___

### moveBefore

▸ **moveBefore**(`item`, `before`): `void`

Move `item` so it is immediately before `before` in this list: places `item` at the index that `before` used
to occupy. Depending on the position in the list `item` originally occupied, some other items in the list may
shift to higher or lower indices as a result. No-op if both arguments are the same item.

**`Throws`**

An error if either argument is not contained in this list.

#### Parameters

| Name | Type |
| :------ | :------ |
| `item` | [`PageNode`](PageNode.md) |
| `before` | [`PageNode`](PageNode.md) |

#### Returns

`void`

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[moveBefore](RestrictedItemList.md#movebefore)

___

### remove

▸ **remove**(...`items`): `void`

Remove the items from the list. The items need not be contiguous.

**`Throws`**

If any of the items are not in the list, or if it is illegal to remove any of the items from this parent.

#### Parameters

| Name | Type |
| :------ | :------ |
| `...items` | [`PageNode`](PageNode.md)[] |

#### Returns

`void`

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[remove](RestrictedItemList.md#remove)

___

### toArray

▸ **toArray**(): readonly [`PageNode`](PageNode.md)[]

All items in the list, as a static array. Mutations that occur later are not reflected in an array returned earlier.

#### Returns

readonly [`PageNode`](PageNode.md)[]

#### Inherited from

[RestrictedItemList](RestrictedItemList.md).[toArray](RestrictedItemList.md#toarray)
