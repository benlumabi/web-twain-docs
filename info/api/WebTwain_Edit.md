---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN SDK API Reference - Edit APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Edit APIs
breadcrumbText: Edit
description: Dynamic Web TWAIN SDK Documentation API Reference Edit APIs Page
permalink: /info/api/WebTwain_Edit.html
---

# {WebTwainObject} Edit

The properties and methods on this page live in the namespace {WebTwainObject}. {WebTwainObject} denotes the `WebTwain` instance. Learn about [how to create a web twain object]({{site.indepth}}features/initialize.html#creating-the-webtwain-instance).

**Methods**

|                                                 |
| :---------------------------------------------- | :-------------------------------------- | ----------------------------------------------- | --------------------------------------------------- |
| [`Crop()`](#crop)                               | [`CropToClipboard()`](#croptoclipboard) | [`CutFrameToClipboard()`](#cutframetoclipboard) | [`CutToClipboard()`](#cuttoclipboard)               |
| [`CopyToClipboard()`](#copytoclipboard)         | [`Erase()`](#erase)                     | [`Flip()`](#flip)                               | [`Mirror()`](#mirror)                               |
| [`Rotate()`](#rotate)                           | [`RotateEx()`](#rotateex)               | [`RotateLeft()`](#rotateleft)                   | [`RotateRight()`](#rotateright)                     |
| [`ChangeBitDepth()`](#changebitdepth)           | [`SetDPI()`](#setdpi)                   | [`ConvertToBW()`](#converttobw)                 | [`ConvertToGrayScale()`](#converttograyscale)       |
| [`ChangeImageSize()`](#changeimagesize)         | [`Invert()`](#invert)                   | [`SetImageWidth()`](#setimagewidth)             | [`ChangeBrightnessAsync()`](#changebrightnessasync) |
| [`ChangeContrastAsnyc()`](#changecontrastasnyc) |

<!--
* [Crop()](#crop)
* [CropToClipboard()](#croptoclipboard)
* [CutFrameToClipboard()](#cutframetoclipboard)
* [CutToClipboard()](#cuttoclipboard)
* [CopyToClipboard()](#copytoclipboard)
* [Erase()](#erase)
* [Flip()](#flip)

<!--* [FlipAsync()](#flipasync)

* [Mirror()](#mirror)

<!--* [MirrorAsync()](#mirrorasync)

* [Rotate()](#rotate)

<!--* [RotateAsync()](#rotate)

* [RotateEx()](#rotateex)
* [RotateLeft()](#rotateleft)

<!--* [RotateLeftAsync()](#rotateleft)

* [RotateRight()](#rotateright)

<!--* [RotateRightAsync()](#rotateright)

* [ChangeBitDepth()](#changebitdepth)
* [SetDPI()](#setdpi)
* [ConvertToBW()](#converttobw)
* [ConvertToGrayScale()](#converttograyscale)

<!--* [ConvertToGrayScaleAsync()](#converttograyscaleasync)
* [ChangeImageSize()](#changeimagesize)
* [Invert()](#invert)
* [SetImageWidth()](#setimagewidth) -->

**Properties**

|                                               |
| :-------------------------------------------- |
| [`BackgroundFillColor`](#backgroundfillcolor) |

## ChangeBitDepth

Change the bit depth of the specified image.

**Syntax**

```javascript
ChangeBitDepth(
    index: number,
    bitDepth: number,
    highQuality: boolean,
): boolean;
```

**Parameters**

`index`: Specify the index of the image to be changed. The index is 0-based.

`bitDepth`: Specify the target bit depth.

`highQuality`: Whether to keep high quality. When it's true, it takes more time.

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v10.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">not supported </td>
</tr>

</table>
</div>

**Usage notes**

The allowed bit depths are 1, 4, 8, 24.

---

## ChangeImageSize

Change the size of the specified image.

**Syntax**

```javascript
ChangeImageSize(
    index: number,
    width: number,
    height: number,
    method: Dynamsoft.DWT.EnumDWT_InterpolationMethod | number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Parameters**
`index`: Specify  the index of the image to be changed. The index is 0-based.

`width`: Specify the new width.

`height`: Specify the new height.

`method`: Specify the algorithm for the change. Please refer to [EnumDWT_InterpolationMethod]({{{site.info}}api/Dynamsoft_Enum.html#dynamsoftdwtenumdwt_interpolationmethod).

`successCallback`: A callback function that is executed if the request succeeds.

`failureCallback`: A callback function that is executed if the request fails.
 * `errorCode`: The error code.
 * `errorString`: The error string.


**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

## SetDPI

Change the DPI (dots per inch) of the specified image.

**Syntax**

```javascript
SetDPI(
    index: number,
    xResolution: number,
    yResolution: number,
    resample: boolean,
    method: Dynamsoft.DWT.EnumDWT_InterpolationMethod | number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Parameters**

`index`: Specify the index of the image to be changed. The index is 0-based.

`xResolution`: Specify the horizontal DPI.

`yResolution`: Specify the vertical DPI.

`resample`: Whether to resample the image. When it is true, the image size will change.

`method`: Specify the algorithm for the change. Please refer to [EnumDWT_InterpolationMethod]({{{site.info}}api/Dynamsoft_Enum.html#dynamsoftdwtenumdwt_interpolationmethod).

`successCallback`: A callback function that is executed if the request succeeds.

`failureCallback`: A callback function that is executed if the request fails.
 * `errorCode`: The error code.
 * `errorString` The error string.


**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v8.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>


---

## ConvertToBW

Convert the specified image to black & white.

**Syntax**

```javascript
ConvertToBW(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Parameters**

`index`: Specify the index of the image to be converted. The index is 0-based.

`successCallback`: A callback function that is executed if the request succeeds.

`failureCallback`: A callback function that is executed if the request fails.
 * `errorCode`: The error code.
 * `errorString`: The error string.


**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">not supported</td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
</tr>

</table>
</div>

---

## ConvertToGrayScale

Convert the specified image to grayscale.

**Syntax**

```javascript
ConvertToGrayScale(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Parameters**

`index`: Specify the index of the image to be converted. The index is 0-based.

`successCallback`: A callback function that is executed if the request succeeds.

`failureCallback`: A callback function that is executed if the request fails.
 * `errorCode`: The error code.
 * `errorString`: The error string.

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v10.0+</td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

<!--

## ConvertToGrayScaleAsync

**Syntax**

``` typescript
/**
 * Convert the specified image to grayscale.
 * @param index Specify the image.
 */
ConvertToGrayScaleAsync(
    index: number
): Promise<boolean>;
```

----->

## Invert

**Syntax**

```typescript
/**
 * Invert the colour of the pixels on the specified image.
 * @param index Specify the image.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Invert(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">not supported </td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
<td align="center">v15.3+ </td>
</tr>

</table>
</div>

---

## SetImageWidth

**Syntax**

```typescript
/**
 * Change the width of the specified image by adding a margin or removing part of the image.
 * @param index Specify the image.
 * @param width Specify the new width.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
SetImageWidth(
    index: number,
    width: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v10.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

## Flip

**Syntax**

```typescript
/**
 * Flip the specified image.
 * @param index Specify the image.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Flip(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

<!--

## FlipAsync

**Syntax**

``` typescript
/**
 * Flip the specified image.
 * @param index Specify the image.
 */
FlipAsync(
    index: number
): Promise<boolean>;
```

--->

## Mirror

**Syntax**

```typescript
/**
 * Mirror the specified image.
 * @param index Specify the image.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Mirror(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

<!--

## MirrorAsync

**Syntax**

``` typescript
/**
 * Mirror the specified image.
 */
MirrorAsync(
    index: number
): Promise<boolean>;
```

--->

## RotateLeft

**Syntax**

```typescript
/**
 * Rotate the specified image 90 degrees counterclockwise.
 * @param index Specify the image.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
RotateLeft(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>
---

<!--

## RotateLeftAsync

**Syntax**

``` typescript
/**
 * Rotate the specified image 90 degrees counterclockwise.
 * @param index Specify the image.
 */
RotateLeftAsync(
    index: number
): Promise<boolean>;
```

--->

## RotateRight

**Syntax**

```typescript
/**
 * Rotate the specified image 90 degrees clockwise.
 * @param index Specify the image.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
RotateRight(
    index: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

<!--

## RotateRightAsync

**Syntax**

``` typescript
/**
 * Rotate the specified image 90 degrees clockwise.
 */
RotateRightAsync(
    index: number
): Promise<boolean>;
```

--->

## Rotate

**Syntax**

```typescript
/**
 * Rotate the specified image by the specified angle.
 * @param index Specify the image.
 * @param angle Specify the angle.
 * @param keepSize Whether to keep the original size.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Rotate(
    index: number,
    angle: number,
    keepSize: boolean,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

<!--

## RotateAsync

**Syntax**

``` typescript
/**
 * Rotate the specified image by the specified angle.
 * @param index Specify the image.
 * @param angle Specify the angle.
 * @param keepSize Whether to keep the original size.
 */
RotateAsync(
    index: number,
    angle: number,
    keepSize: boolean
): Promise<boolean>;
```

--->

## RotateEx

**Syntax**

```typescript
/**
 * Rotate the specified image by the specified angle.
 * @param index Specify the image.
 * @param angle Specify the angle.
 * @param keepSize Whether to keep the original size.
 * @param method Specify the algorithm for the change.
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
RotateEx(
    index: number,
    angle: number,
    keepSize: boolean,
    method: Dynamsoft.DWT.EnumDWT_InterpolationMethod | number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v7.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

**Usage notes**

Check out [ `Dynamsoft.DWT.EnumDWT_InterpolationMethod` ]({{site.info}}api/Dynamsoft_Enum.html#dynamsoftdwtenumdwt_interpolationmethod).

---

## Crop

**Syntax**

```typescript
/**
 * Crop the specified image using the specified coordinates.
 * @param index Specify the image.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param right Specify the rectangle (rightmost coordinate).
 * @param bottom Specify the rectangle (bottommost coordinate).
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Crop(
    index: number,
    left: number,
    top: number,
    right: number,
    bottom: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

## Erase

**Syntax**

```typescript
/**
 * Erase a rectangular area from the specified image.
 * @param index Specify the image.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param right Specify the rectangle (rightmost coordinate).
 * @param bottom Specify the rectangle (bottommost coordinate).
 * @param successCallback A callback function that is executed if the request succeeds.
 * @param failureCallback A callback function that is executed if the request fails.
 * @argument errorCode The error code.
 * @argument errorString The error string.
 */
Erase(
    index: number,
    left: number,
    top: number,
    right: number,
    bottom: number,
    successCallback?: () => void,
    failureCallback?: (
        errorCode: number,
        errorString: string
    ) => void
): void | boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

---

## CopyToClipboard

**Syntax**

```typescript
/**
 * Copy the specified image to the clipboard of the operating system.
 * @param index Specify the image.
 */
CopyToClipboard(index: number): boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>


---

<!--

## CopyToClipboardAsync

**Syntax**

``` typescript
/**
 * Copy the specified image to the clipboard of the operating system.
 * @param index Specify the image.
 */
CopyToClipboardAsync(index: number): Promise<boolean>;
```

--->

## CutToClipboard

**Syntax**

```typescript
/**
 * Cut the specified image to the clipboard of the operating system.
 * @param index Specify the image.
 */
CutToClipboard(index: number): boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<>
align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
<td align="center">not supported </td>
</tr>

</table>
</div>


---

## CropToClipboard

**Syntax**

```typescript
/**
 * Crop a rectangular area from the specified image to the clipboard of the operating system.
 * @param index Specify the image.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param right Specify the rectangle (rightmost coordinate).
 * @param bottom Specify the rectangle (bottommost coordinate).
 */
CropToClipboard(
    index: number,
    left: number,
    top: number,
    right: number,
    bottom: number
): boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v4.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>


---

## CutFrameToClipboard

**Syntax**

```typescript
/**
 * Cut a rectangular area from the specified image to the clipboard of the operating system.
 * @param index Specify the image.
 * @param left Specify the rectangle (leftmost coordinate).
 * @param top Specify the rectangle (topmost coordinate).
 * @param right Specify the rectangle (rightmost coordinate).
 * @param bottom Specify the rectangle (bottommost coordinate).
 */
CutFrameToClipboard(
    index: number,
    left: number,
    top: number,
    right: number,
    bottom: number
): boolean;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>


**Usage notes**

The empty area resulted from the crop/erase/cut will be filled with the colour set with [BackgroundFillColor](#backgroundfillcolor).

---

## BackgroundFillColor

**Syntax**

```typescript
/**
 * Return or set the fill colour for the empty area on an image that has been cut/cropped/erased.
 */
BackgroundFillColor: number;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">v6.0+ </td>
<td align="center">v10.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v11.0+ </td>
<td align="center">v12.1+ </td>
</tr>

</table>
</div>

**Usage notes**

By default the colour is white (0xffffff). The byte-ordering of the 24-bit RGB value is **RRGGBB**. RR represents red, GG represents green and BB represents blue.

---

## ChangeBrightnessAsync

**Syntax**

```typescript
/**
 * Change the image brightness.
 * @param index Specify the index of image in buffer.
 * @param val Specify the brightness. Allowed values [-1000~1000]. Negative value means decrease the brightness.
 */
ChangeBrightnessAsync(index: number, val: number): Promise<boolean>;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">not supported  </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
</tr>

</table>
</div>

---

## ChangeContrastAsnyc

**Syntax**

```typescript
/**
 * Change the image contrast.
 * @param index Specify the index of image in buffer.
 * @param val Specify the contrast. Allowed values [-1000~1000]. Negative value means decrease the contrast.
 */
ChangeContrastAsnyc(index: number, val: number): Promise<boolean>;
```

**Availability**
<div class="availability">
<table>

<tr>
<td align="center">ActiveX</td>
<td align="center">H5(Windows)</td>
<td align="center">H5(macOS/TWAIN)</td>
<td align="center">H5(macOS/ICA)</td>
<td align="center">H5(Linux)</td>
</tr>

<tr>
<td align="center">not supported  </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
</tr>

</table>
</div>
