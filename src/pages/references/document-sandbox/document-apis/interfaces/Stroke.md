[@express-document-sdk](../overview.md) / Stroke

# Interface: Stroke

Represents a stroke in the scenegraph. See [StrokableNode](../classes/StrokableNode.md).

## Hierarchy

- [`StrokeOptions`](StrokeOptions.md)

  ↳ **`Stroke`**

## Table of contents

### Properties

- [color](Stroke.md#color)
- [dashOffset](Stroke.md#dashoffset)
- [dashPattern](Stroke.md#dashpattern)
- [position](Stroke.md#position)
- [width](Stroke.md#width)

## Properties

### color

• `Readonly` **color**: [`Color`](../classes/Color.md)

The color of a stroke.

#### Inherited from

[StrokeOptions](StrokeOptions.md).[color](StrokeOptions.md#color)

___

### dashOffset

• `Readonly` **dashOffset**: `number`

Number of pixels the beginning of dash pattern should be offset along the stroke.

#### Inherited from

[StrokeOptions](StrokeOptions.md).[dashOffset](StrokeOptions.md#dashoffset)

___

### dashPattern

• `Readonly` **dashPattern**: `number`[]

If empty, this is a solid stroke.
If non-empty, the values alternate between length of a rendered and blank segment,
repeated along the length of the stroke. The first value represents the first solid segment.

#### Inherited from

[StrokeOptions](StrokeOptions.md).[dashPattern](StrokeOptions.md#dashpattern)

___

### position

• `Readonly` **position**: [`StrokePosition`](../enums/StrokePosition.md)

The position of the stroke relative to the outline of the shape.

___

### width

• `Readonly` **width**: `number`

The thickness of a stroke. Must be from MIN_STROKE_WIDTH to MAX_STROKE_WIDTH.

#### Inherited from

[StrokeOptions](StrokeOptions.md).[width](StrokeOptions.md#width)
