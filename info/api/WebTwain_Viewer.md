---
layout: default-layout
needAutoGenerateSidebar: true
title: Dynamic Web TWAIN SDK API Reference - Viewer APIs
keywords: Dynamic Web TWAIN, Documentation, API Reference, Viewer APIs
breadcrumbText: Viewer
description: Dynamic Web TWAIN SDK Documentation API Reference Viewer APIs Page
permalink: /info/api/WebTwain_Viewer.html
---

# `{WebTwainObject}.Viewer`

> {WebTwainObject} denotes the `WebTwain` instance.

**Methods**

|                                                     |
| :-------------------------------------------------- | :-------------------------------------------- | ----------------------------------------------- | ------------------------------------------- |
| [`bind()`](#bind)                                   | [`clearSelectedAreas()`](#clearselectedareas) | [`createCustomElement()`](#createcustomelement) | [`createImageEditor()`](#createimageeditor) |
| [`createThumbnailViewer()`](#createthumbnailviewer) | [`first()`](#first)                           | [`fitWindow()`](#fitwindow)                     | [`gotoPage()`](#gotopage)                   |
| [`hide()`](#hide)                                   | [`last()`](#last)                             | [`next()`](#next)                               | [`off()`](#off)                             |
| [`on()`](#on)                                       | [`previous()`](#previous)                     | [`render()`](#render)                           | [`setButtonClass()`](#setbuttonclass)       |
| [`setSelectedAreas()`](#setselectedareas)           | [`setViewMode()`](#setviewmode)               | [`show()`](#show)                               | [`unbind()`](#unbind)                       |
| [`createTemplate()`](#createtemplate)               | [`createDocumentEditor()`](#createdocumenteditor)   | [`updateCheckboxStyle()`](#updatecheckboxstyle)     | [`updatePageNumberStyle()`](#updatepagenumberstyle)       |

**Properties**

|                                             |
| :------------------------------------------ | :------------------------------------------------------ | ----------------------------------------------------- | --------------------------------------------------- |
| [`acceptDrop`](#acceptdrop)                 | [`allowSlide`](#allowslide)                             | [`allowPageDragging`](#allowpagedragging)             | [`background`](#background)                         |
| [`border`](#border)                         | [`cursor`](#cursor)                                     | [`height`](#height)                                   | [`idPostfix`](#idpostfix)                           |
| [`ifAutoScroll`](#ifautoscroll)             | [`innerBorder`](#innerborder)                           | [`pageMargin`](#pagemargin)                           | [`selectedAreaBorderColor`](#selectedareabordercolor) |
| [`selectedPageBackground`](#selectedpagebackground) | [`selectedPageBorder`](#selectedpageborder)     | [`selectionRectAspectRatio`](#selectionrectaspectratio) | [`singlePageMode`](#singlepagemode)               |
| [`width`](#width)                           | [`zoom`](#zoom)                                         | [`autoChangeIndex`](#autochangeindex)                 | [`selectionMode`](#selectionmode)                   |

**Events**

|                                 |
| :------------------------------ | :---------------------------- | --------------------------------------- | ------------------------------------------- |
| [`click`](#click)               | [`contextmenu`](#contextmenu) | [`dblclick`](#dblclick)                 | [`mousemove`](#mousemove)                   |
| [`mousedown`](#mousedown)       | [`mouseup`](#mouseup)         | [`mouseout`](#mouseout)                 | [`mouseover`](#mouseover)                   |
| [`keydown`](#keydown)           | [`keyup`](#keyup)             | [`pageAreaSelected`](#pageareaselected) | [`pageAreaUnselected`](#pageareaunselected) |
| [`pageRendered`](#pagerendered) | [`resize`](#resize)           |

---

## bind

**Syntax**

```typescript
/**
 * Create a Dynamsoft Viewer instance and bind it to the WebTwain instance.
 * @param element Specify an HTML element to create the viewer.
 * @param documentTemplate Specify the document template.
 */
bind(element: HTMLDivElement, documentTemplate: DocumentViewerTemplate) : void;

interface DocumentViewerTemplate{
   getCustomElement():CustomElement; //Get CustomElement. Can display save & upload interface in CustomElement.
   onAddDocumentFunc = function () {}
   onExitFunc = function () {}
   onSaveFunc = function () {} //Save button click event
   onUploadFunc = function () {}  //Upload button click event
   onRemoveSelectedFunc = function () {}   //Remove button click event
}
```

**Example**

```javascript
var DWObject, template;
Dynamsoft.DWT.CreateDWTObjectEx(
  {
    WebTwainId: "a",
    UseLocalService: false,
  },
  function (obj) {
    DWObject = obj;
    template = DWObject.Viewer.createTemplate("documentScanner");
    DWObject.Viewer.bind(null, template); //full screen
    DWObject.Viewer.show(); 
  
    template.onExitFunc = function () {
    DWObject.Viewer.show();   
    console.error ("execute");
    //RemoveAllFile();     
}
}, function (errorCode, errorString) {
    console.log(errorString);
  });
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
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
<td align="center">v17.2+ </td>
</tr>

</table>
</div>

**Usage notes**

Replace the previous `BindViewer` method.

---

## clearSelectedAreas

**Syntax**

```typescript
/**
 * Clear the selected area(s) on the current page.
 */
clearSelectedAreas(): void;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.clearSelectedAreas();
```

---

## createCustomElement

**Syntax**

```typescript
/**
 * Add a custom page DIV element and specify its position and display order.
 * Generate an independent CustomElement object.
 * @param element Specify the HTMLDivElement.
 * @param location Define where to place the custom element. The allowed values are "left" and "right", and the default value is "right".
 * @param bCover The default value is `false`, that is, the created CustomElement is displayed according to the set area. If set to true, the main viewer will be covered by the CustomElement.
 */
createCustomElement(
    element: HTMLDivElement,
    location?: string,
    bCover?: boolean
): CustomElement;

interface CustomElement {
    /**
     * Show the custom element.
     */
    show(): boolean;
    /**
     * Hide the custom element.
     */
    hide(): boolean;
    /**
     * Remove the custom element.
     */
    dispose(): boolean;
};
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
var myElement = document.createElement("div");
myElement.style = "width:100px;height:200px;background:red";
var customElement = DWObject.Viewer.createCustomElement(
  myElement,
  "right",
  false
);
customElement.show();
```

**Usage notes**

Only one CustomElement object can be created. If you try creating another one, you'll get the error 'A CustomElement already exists.', and the existing CustomElement object will be returned.

If the width defined by the CustomElement object exceeds the width of the main viewer, the width of the main viewer is used.

The method [ `unbind()` ](#unbind) will dispose all created CustomElement objects, ThumbnailViewer objects and ImageEditor objects.

---

## createImageEditor

**Syntax**

```typescript
/**
 * Generate an independent ImageEditor object.
 * @param editorSettings Configure the object.
 */
createImageEditor(
    editorSettings?: EditorSettings
): ImageEditor;

interface ImageEditor {
    /**
     * Show the ImageEditor object.
     */
    show(): boolean;
    /**
     * Hide the ImageEditor object.
     */
    hide(): boolean;
    /**
     * Remove the ImageEditor object.
     */
    dispose(): boolean;
};
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

> The example code shows 2 ways to use the API `createImageEditor()`

```javascript
// Use default settings
var imageEditor = DWObject.Viewer.createImageEditor();
imageEditor.show();
```

```javascript
// Customize the editor
var editorSettings = {
  /* Show the editor within the DIV 'imageEditor'*/
  element?: document.getElementById("imageEditor"),
  width?: 600,
  height?: 400,
  border?: "1px solid rgb(204, 204, 204)",
  topMenuBorder?: "",
  innerBorder?: "",
  background?: "rgb(255, 255, 255)",
  promptToSaveChange?: true,
  buttons?: {
    titles?: {
      previous?: "Previous Image",
      next?: "Next Image",
      print?: "Print Image",
      scan?: "Scan Documents",
      load?: "Load Local Images",
      rotateleft?: "Rotate Left",
      rotate?: "Rotate",
      rotateright?: "Rotate Right",
      deskew?: "Deskew",
      crop?: "Crop Selected Area",
      cut?: "Cut Selected Area",
      changeimagesize?: "Change Image Size",
      flip?: "Flip Image",
      mirror?: "Mirror Image",
      zoomin?: "Zoom In",
      originalsize?: "Show Original Size",
      zoomout?: "Zoom Out",
      stretch?: "Stretch Mode",
      fit?: "Fit Window",
      fitw?: "Fit Horizontally",
      fith?: "Fit Vertically",
      hand?: "Hand Mode",
      rectselect?: "Select Mode",
      zoom?: "Click to Zoom In",
      restore?: "Restore Original Image",
      save?: "Save Changes",
      close?: "Close the Editor",
      removeall?: "Remove All Images",
      removeselected?: "Remove All Selected Images",
    },
    visibility?: {
      scan?: true,
      load?: true,
      print?: true,
      removeall?: true,
      removeselected?: true,
      rotateleft?: true,
      rotate?: true,
      rotateright?: true,
      deskew?: true,
      crop?: true,
      cut?: true,
      changeimagesize?: true,
      flip?: true,
      mirror?: true,
      zoomin?: true,
      originalsize?: true,
      zoomout?: true,
      stretch?: true,
      fit?: true,
      fitw?: true,
      fith?: true,
      hand?: true,
      rectselect?: true,
      zoom?: true,
      restore?: true,
      save?: true,
      close?: true,
    },
  },
  dialogText?: {
    dlgRotateAnyAngle?: [
      "Angle :",
      "Interpolation:",
      "Keep size",
      "  OK  ",
      "Cancel",
    ],
    dlgChangeImageSize?: [
      "New Height :",
      "New Width :",
      "Interpolation method:",
      "  OK  ",
      "Cancel",
    ],
    saveChangedImage?: [
      "You have changed the image, do you want to keep the change(s)?",
      "  Yes  ",
      "  No  ",
    ],
    selectSource?: [
      "Select Source:",
      "Select",
      "Cancel",
      "There is no source available",
    ],
  },
};

var imageEditor = DWObject.Viewer.createImageEditor(editorSettings);
imageEditor.show();
```

**Usage notes**

Replace the previous `ShowImageEditor()` method.

Only one ImageEditor object can be created. If you try creating it again, you'll get the error 'An ImageEditor already exists.' and the existing ImageEditor object will be returned.

The method [ `unbind()` ](#unbind) will dispose all created CustomElement objects, ThumbnailViewer objects and ImageEditor objects.

---

## createThumbnailViewer

**Syntax**

<div class="sample-code-prefix template2"></div>

>- 17.3+
>- 17.2.5
>
```typescript
/**
 * Generate a independent ThumbnailViewer object.
 * @param thumbnailViewerSettings Configure the ThumbnailViewer object
 */
createThumbnailViewer(
    thumbnailViewerSettings?: ThumbnailViewerSettings
): ThumbnailViewer;
interface ThumbnailViewer {
    /**
     * Show the ThumbnailViewer object.
     */
    show(): boolean;
    /**
     * Hide the ThumbnailViewer object.
     */
    hide(): boolean;
    /**
     * Remove the ThumbnailViewer object.
     */
    dispose(): boolean;
    /**
     * Change the view mode of the thumbnail viewer.
     * @param viewMode Specify the new mode.
     */
    updateViewMode(viewMode: ViewMode): void;
    /**
     * Change the checkbox style. Available in v17.3+.
     * @param checkboxSettings Specify the checkbox settings.
     */
    updateCheckboxStyle(checkboxSettings?: CheckboxSettings): void;
    /**
     * Change the page number style. Available in v17.3+.
     * @param pageNumberSettings Specify the page number settings.
     */
    updatePageNumberStyle(pageNumberSettings?: PageNumberSettings): void;
    /**
     * Bind a listner to the specified event. You can bind one or multiple listeners to the same event.
     * @param eventName Specify the event name.
     * @param callback Specify the listner.
     */
    on(eventName: string, callback: (event: ThumbnailViewerEvent | KeyboardEvent, domEvent?: MouseEvent) => void): void;
    /**
     * Unbind event listener(s) from the specified viewer event.
     * @param eventName Specify the event.
     * @param callback Specify the listener to remove
     */
    off(eventName: string, callback?: () => void): void;
}
interface ThumbnailViewerSettings {
    /**
     * Specify how many images to display per row.
     */  
    columns?: number;
    /**
     * Specify how many images to display per column.
     */  
    rows?: number;    
    /**
     * Whether to allow keyboard control. Default: true.
     */  
    allowKeyboardControl?: boolean;
    /**
     * Whether to allow page dragging to reorder the pages.
     * Default: true.
     */
    allowPageDragging?: boolean;
    /**
     * Whether to allow resizing of the thumbnail viewer.
     * Default: false.
     */
    allowResizing?: boolean;
    /**
     * Set or return the CSS rule for the background of the thumbnail viewer.
     * Default: "rgb(255, 255, 255)".
     */
    background?: string;
    /**
     * Set or return the CSS rule for the border of the thumbnail viewer.
     * Default: "".
     */
    border?: string;
    /**
     * Set or return the CSS rule for the background of the page the mouse hovers over in the thumbnail viewer.
     * Default: "rgb(239, 246, 253)".
     */
    hoverPageBackground?: string;
    /**
     * Set or return the CSS rule for the border of the page the mouse hovers over in the thumbnail viewer.
     * Default: "1px solid rgb(238, 238, 238)".
     */
    hoverPageBorder?: string;
    /**
     * Set or return the location of the thumbnail viewer. Allowed values are "left", "right", "top", "bottom".
     * Default: "left".
     */
    location?: string;
    /**
     * Set or return the CSS rule for the background of a normal page in the thumbnail viewer.
     * Default: "transparent".
     */
    pageBackground?: string;
    /**
     * Set or return the CSS rule for the border of a normal page in the thumbnail viewer.
     * Default: "1px solid rgb(238, 238, 238)".
     */
    pageBorder?: string;
    /**
     * Set or return the margin between two adjacent images and the margin between an image and the border of the thumbnail viewer. The value can either be in pixels or percentage.
     * Default: 10.
     */
    pageMargin?: number | string;
    /**
     * Set or return the CSS rule for the background of the placeholder which appears when you drag page(s) to reorder them in the thumbnail viewer.
     * Default: "rgb(251, 236, 136)".
     */
    placeholderBackground?: string;
    /**
     * Set or return whether the pages are arranged vertically or horizontally.
     * Default: "vertical". Allowed values are "vertical" and "horizontal".
     */
    scrollDirection?: string;
    /**
     * Set or return the CSS rule for the background of the selected page(s) in the thumbnail viewer.
     * Default: "rgb(199, 222, 252)".
     */
    selectedPageBackground?: string;
    /**
     * Set or return the CSS rule for the border of the selected page(s) in the thumbnail viewer.
     * Default: "1px solid rgb(125,162,206)".
     */
    selectedPageBorder?: string;
    /**
     * Set or return the size of the thumbnail viewer. The value can either be in pixels or percentage (based on the width or height of the entire viewer).
     * Default: "30%".
     */
    size?: number | string;
    /**
     * Set whether to select the index in the upper left corner of the viewer when scrolling.
     * Default: false.
     */
    autoChangeIndex?: boolean;
    checkbox?: {
      visibility?: string; //"visible":hidden", default: "hidden" 
      width?: number | string; //default: "24px",number unit: px, string value: "24px"/"10%", relative to parent container
      height?: number | string; //default: "24px",number unit: px, string value: "24px"/"10%", relative to parent container
      background?: string; //default: "#ffffff"
      borderWidth?: number | string;  //default: "2px", unit: px, percentage value not supported
      borderColor?: string; //default: "#000000"
      checkMarkColor?: string; //default: "#000000"
      checkMarkLineWidth?: number | string; //default: "2px", unit: px, percentage value not supported
      borderRadius?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%",relative to itself
      opacity?: number; //default:0.5, value range [0-1], value greater 1 defaults to 1
      left?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
      top?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
      right?: number | string;  //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
      bottom?: number | string;  //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
      translateX?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to itself
      translateY?: number | string //default: "",  number unit: px, string value: "10px"/"10%", relative to itself
    };
    pageNumber?: {
      visibility?: string; //"visible": hidden", default: "hidden" 
      width?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
      height?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
      background?: string; //default: "#ffffff"            
      borderWidth?: number | string; //default: "1px", unit: px, percentage value not supported
      borderColor?: string; //default: "#a79898"
      borderRadius?: number | string; //default: "50%", number unit: px, string value: "10px"/"10%", relative to itself
      opacity?:number; //default: 0.5, value range [0-1], value greater 1 defaults to 1
      color?: string; //default: "#000000", supports #16 hexadecimal only
      fontFamily?: string; //default: "sans-serif"
      fontSize?: number | string; //default: 12, unit: px, percentage value not supported
      left?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
      top?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
      right?: number | string; //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
      bottom?: number | string; //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
      translateX?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to itself
      translateY?: number | string //default: "", number unit: px, string value: "10px"/"10%", relative to itself
    }
};
interface ThumbnailViewerEvent {
    // The index of the current page.
    index: number;
    // The x-coordinate of the browser page.
    pageX: number;
    // The y-coordinate of the browser page.
    pageY: number;
};
interface ViewMode {
    /**
     * Specify the number of images per row.
     */
    columns: number;
    /**
     * Specify the number of images per column.
     */
    rows: number;
    /**
     * Set or return whether the pages are arranged vertically or horizontally.
     * Default: "vertical". Allowed values are "vertical" and "horizontal".
     */
    scrollDirection: string;
}
```
```typescript
/** 
 * Generate a independent ThumbnailViewer object. 
 * @param thumbnailViewerSettings Configure the ThumbnailViewer object 
 */ 
createThumbnailViewer( 
    thumbnailViewerSettings?: thumbnailViewerSettings 
): ThumbnailViewer; 
interface ThumbnailViewer { 
    /** 
    * Show the ThumbnailViewer object. 
    */ 
    show(): boolean; 
    /** 
    * Hide the ThumbnailViewer object. 
    */ 
    hide(): boolean; 
    /** 
    * Remove the ThumbnailViewer object. 
    */ 
    dispose(): boolean; 
    /** 
    * Change the view mode of the thumbnail viewer. 
    * @param viewMode Specify the new mode. 
    */ 
    updateViewMode(viewMode: ViewMode): void; 
    /** 
    * Bind a listner to the specified event. You can bind one or multiple listeners to the same event. 
    * @param eventName Specify the event name. 
    * @param callback Specify the listner. 
    */ 
    on(eventName: string, callback: (event: ThumbnailViewerEvent | KeyboardEvent, domEvent?: MouseEvent) => void): void; 
    /** 
    * Unbind event listener(s) from the specified viewer event. 
    * @param eventName Specify the event. 
    * @param callback Specify the listener to remove 
    */ 
    off(eventName: string, callback?: () => void): void; 
    /** 
    * Whether to allow keyboard control. Default: true. 
    */ 
    allowKeyboardControl: boolean; 
    /** 
    * Whether to allow page dragging to reorder the pages. 
    * Default: true. 
    */ 
    allowPageDragging: boolean; 
    /** 
    * Whether to allow resizing of the thumbnail viewer. 
    * Default: false. 
    */ 
    allowResizing: boolean; 
    /** 
    * Set or return the CSS rule for the background of the thumbnail viewer. 
    * Default: "rgb(255, 255, 255)". 
    */ 
    background: string; 
    /** 
    * Set or return the CSS rule for the border of the thumbnail viewer. 
    * Default: "". 
    */ 
    border: string; 
    /** 
    * Set or return the CSS rule for the background of the page the mouse hovers over in the thumbnail viewer. 
    * Default: "rgb(239, 246, 253)". 
    */ 
    hoverPageBackground: string; 
    /** 
    * Set or return the CSS rule for the border of the page the mouse hovers over in the thumbnail viewer. 
    * Default: "1px solid rgb(238, 238, 238)". 
    */ 
    hoverPageBorder: string; 
    /** 
    * Set or return the location of the thumbnail viewer. Allowed values are "left", "right", "top", "bottom". 
    * Default: "left". 
    */ 
    location: string; 
    /** 
    * Set or return the CSS rule for the background of a normal page in the thumbnail viewer. 
    * Default: "transparent". 
    */ 
    pageBackground: string; 
    /** 
    * Set or return the CSS rule for the border of a normal page in the thumbnail viewer. 
    * Default: "1px solid rgb(238, 238, 238)". 
    */ 
    pageBorder: string; 
    /** 
    * Set or return the margin between two adjacent images and the margin between an image and the border of the thumbnail viewer. The value can either be in pixels or percentage. 
    * Default: 10. 
    */ 
    pageMargin: number | string; 
    /** 
    * Set or return the CSS rule for the background of the placeholder which appears when you drag page(s) to reorder them in the thumbnail viewer. 
    * Default: "rgb(251, 236, 136)". 
    */ 
    placeholderBackground: string; 
    /** 
    * Set or return whether the pages are arranged vertically or horizontally. 
    * Default: "vertical". Allowed values are "vertical" and "horizontal". 
    */ 
    scrollDirection: string; 
    /** 
    * Set or return the CSS rule for the background of the selected page(s) in the thumbnail viewer. 
    * Default: "rgb(199, 222, 252)". 
    */ 
    selectedPageBackground: string; 
    /** 
    * Set or return the CSS rule for the border of the selected page(s) in the thumbnail viewer. 
    * Default: "1px solid rgb(125,162,206)". 
    */ 
    selectedPageBorder: string; 
    /** 
    * Set or return whether page numbers are shown. 
    * Default: false. 
    */ 
    showPageNumber: boolean; 
    /** 
    * Set or return the size of the thumbnail viewer. The value can either be in pixels or percentage (based on the width or height of the entire viewer). 
    * Default: "30%". 
    */ 
    size: number | string; 
    /** 
    * Set whether to select the index in the upper left corner of the viewer when scrolling. 
    * Default: false. 
    */ 
    autoChangeIndex: boolean; 
    /** 
    * Show checkbox on image(s). 
    */ 
    showCheckbox: boolean; 
}; 
interface ThumbnailViewerEvent { 
    // The index of the current page. 
    index: number; 
    // The x-coordinate of the browser page. 
    pageX: number; 
    // The y-coordinate of the browser page. 
    pageY: number; 
}; 
interface ViewMode { 
    /** 
    * Specify the number of images per row. 
    */ 
    columns: number; 
    /** 
    * Specify the number of images per column. 
    */ 
    rows: number; 
    /** 
    * Set or return whether the pages are arranged vertically or horizontally. 
    * Default: "vertical". Allowed values are "vertical" and "horizontal". 
    */ 
    scrollDirection: string; 
}
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

> The example code shows 2 ways to use the API `createThumbnailViewer()`

```javascript
// Use default settings
var objThumbnailViewer = DWObject.Viewer.createThumbnailViewer();
objThumbnailViewer.background = "rgb(0,0,255)";
objThumbnailViewer.show();
```

```javascript
// Customize the thumbnail viewer
var thumbnailViewerSettings = {
    location: 'left',
    size: '30%',
    columns: 1,
    rows: 3,
    scrollDirection: 'vertical', // 'horizontal'
    pageMargin: 10,
    background: "rgb(255, 255, 255)",
    border: '',
    allowKeyboardControl: true,
    allowPageDragging: true,
    allowResizing: false,
    pageBackground: "transparent",
    pageBorder: "1px solid rgb(238, 238, 238)",
    hoverBackground: "rgb(239, 246, 253)",
    hoverPageBorder: "1px solid rgb(238, 238, 238)",
    placeholderBackground: "rgb(251, 236, 136)",
    selectedPageBorder: "1px solid rgb(125,162,206)",
    selectedPageBackground: "rgb(199, 222, 252)"
}​​​​​​​;

var thumbnail = DWObject.Viewer.createThumbnailViewer(thumbnailViewerSettings);
thumbnail.show();
```

**Usage notes**

For the CheckboxSettings and PageNumberSettings interface, please refer to the APIs [updateCheckboxStyle]({{site.info}}api/WebTwain_Viewer.html#updatecheckboxstyle) and [updatePageNumberStyle]({{site.info}}api/WebTwain_Viewer.html#updatepagenumberstyle).

The following table shows the events available to a ThumbnailViewer object.

| Event Name     | Arguments                                         | Description                                                          |
| :------------- | :------------------------------------------------ | :------------------------------------------------------------------- |
| `click`        | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse is clicked                                  |
| `dblclick`     | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse is double clicked                           |
| `contextMenu`  | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse is right clicked                            |
| `mousemove`    | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse moved over                                  |
| `mousedown`    | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse key is pressed                              |
| `mouseup`      | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse key is released                             |
| `resize`       | width:number, height:number                     | Triggered when width & height of the ThumbnailViewer object changes. |
| `pageRendered` | index: number                                     | Triggered when a page is rendered.                                   |
| `mouseout`     | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when the mouse is out, only for desktop browsers           |
| `mouseover`    | event: ThumbnailViewerEvent, domEvent: MouseEvent | Triggered when mouse is hovering, only for desktop browsers          |
| `keydown`      | keyboardEvent: KeyboardEvent                      | Triggered when a key is pressed, only for desktop browsers           |
| `keyup`        | keyboardEvent: KeyboardEvent                      | Triggered when a key is released, only for desktop browsers          |

By default, scrolling the scroll bar on Thumbnail does not trigger the `topchanged` event.

Only one ThumbnailViewer object can be created. If you try creating it again, you will get the error 'A ThumbnailViewer already exists.' and the existing ThumbnailViewer object will be returned.

The method [ `unbind()` ](#unbind) will dispose all created CustomElement objects, ThumbnailViewer objects and ImageEditor objects.

---

## first

**Syntax**

```typescript
/**
 * Show the first page and return the index which should be 0. If there is no page in the viewer, -1 is returned.
 */
first():number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.first();
```

---

## fitWindow

**Syntax**

```typescript
/**
 * Set how the page is fit in the viewer.
 * @param type Specify how to fit. Allowed values are "width" and "height"
 */
fitWindow(
    type?: string
): void
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.fitWindow();
```

**Usage notes**

This API only works if the view mode of the viewer is set to -1 by -1 ([ `singlePageMode` ](#singlepagemode) is true).

The allowed values are

width: Fit the page vertically.
height: Fit the page horizontally.

If no parameter is provided, it tries to fit the whole page within the viewer.

---

## gotoPage

**Syntax**

```typescript
/**
 * Show the specified page and return its index.
 * @param index Specify the page.
 */
gotoPage(
    index: number
): number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.gotoPage(0);
```

---

## hide

**Syntax**

```typescript
/**
 * Hide the viewer.
 */
hide(): boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.hide();
```

---

## last

**Syntax**

```typescript
/**
 * Show the last page and return its index. If there is no page in the viewer, -1 is returned.
 */
last():number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.last();
```

---

## next

**Syntax**

```typescript
/**
 * Show the next page and return its index. If there is no page in the viewer, -1 is returned.
 */
next(): number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.SelectImages([3]); //Select the 4th page.
var currentIndex = DWObject.Viewer.next(); // return 4 which represents the 5th page.
```

---

## off

**Syntax**

```typescript
/**
 * Unbind event listener(s) from the specified viewer event.
 * @param eventName Specify the event.
 * @param callback Specify the listener to remove
 */
Viewer.off(
    eventName: string,
    callback?: () => void
): void;
```

**Example**

```javascript
DWObject.Viewer.off("pageAreaSelected");
```

**Usage notes**

If no listener is specified, all listeners will be removed.

---

## on

**Syntax**

```typescript
/**
 * Bind a listner to the specified event. You can bind one or multiple listeners to the same event.
 * @param eventName Specify the event name.
 * @param callback Specify the listner.
 */
Viewer.on(
    eventName: string,
    callback: (event: ViewerEvent) => void
): void;
```

**Example**

```javascript
//bind pageAreaSelected event on the main viewer
var callback = function (sImageIndex, rect) {
  console.log(sImageIndex);
};
DWObject.Viewer.on("pageAreaSelected", callback);

//bind click event on the thumbnail viewer
var objThumbnailViewer = DWObject.Viewer.createThumbnailViewer();
objThumbnailViewer.show();
objThumbnailViewer.on("click", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});
```

---

## previous

**Syntax**

```typescript
/**
 * Show the previous page and return its index. If there is no page in the viewer, -1 is returned.
 */
previous(): number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.SelectImages([3]); //Select the 4th page.
var currentIndex = DWObject.Viewer.previous(); // return 2 which represents the 3rd page.
```

---

## render

**Syntax**

```typescript
/**
 * Refresh the viewer.
 */
render(): boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.on("pageRendered", function (index) {
  console.log(index);
});

DWObject.Viewer.render(); //It will trigger the pageRendered event
```

---

## setButtonClass

**Syntax**

``` typescript
/**
 * Set the CSS class name of the specified button.
 * @param name Specify the button.
 * @param className Specify the CSS class name.
 */
setButtonClass(
    name: string,
    className: string
): boolean;
```

**Usage notes**

Use this method to fine-tune the buttons in the viewer with CSS.

**Example**

``` javascript
DWObject.Viewer.setButtonClass("crop", "CropClass");
```

---

## setSelectedAreas

**Syntax**

```typescript
/**
 * Set one or more rectangular area(s) on the current page.
 * @param areas Specify the rectangular area(s).
 */
setSelectedAreas(
    areas: Area[]
): void;

interface Area {
    left: number,
    top: number,
    right: number,
    bottom: number,
};
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.setSelectedAreas([
  {
    left: 0,
    top: 0,
    right: 100,
    bottom: 100,
  },
  {
    left: 200,
    top: 200,
    right: 400,
    bottom: 500,
  },
]);
```

**Usage notes**

The coordinates are based on the size of the original page (instead of the size of the viewer).

This method only works when [ `cursor` ](#cursor) is set to "crosshair".

---

## setViewMode

**Syntax**

```typescript
/**
 * Set the view mode of the viewer.
 * @param columns Specify the number of images per column.
 * @param rows Specify the number of images per row.
 */
setViewMode(
    columns: number,
    rows: number
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
<td align="center">v16.1+ </td>
<td align="center">v16.1+ </td>
<td align="center">v16.1+ </td>
<td align="center">v16.1+ </td>
<td align="center">v16.1+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.setViewMode(2, 2);
```

**Usage notes**

Setting the view mode as -1 by -1 is equivalent to setting [ `singlePageMode` ](#singlepagemode) to true.

---

## show

**Syntax**

```typescript
/**
 * Show the viewer.
 */
show(): boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.show();
```

---

## unbind

**Syntax**

```typescript
/**
 * Unbind and destroy the viewer.
 */
unbind(): boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.unbind();
```

**Usage notes**

Replace the previous `UnbindViewer` method.

---

## acceptDrop

**Syntax**

```typescript
/**
 * Set whether to load files dropped over the viewer area.
 * The default value is true.
 */
acceptDrop: boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

 **Example**

```javascript
DWObject.Viewer.acceptDrop = true;
```

---

## allowSlide

```typescript
/**
 * Set whether to allow image navigation by swiping left or right on the viewer.
 * The default value is true.
 */
allowSlide: boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.allowSlide = true;
```

**Usage notes**

This API only works if the view mode of the viewer is set to -1 by -1.

---

## allowPageDragging

```typescript
/**
 * Set whether to allow page dragging to reorder the pages in the viewer.
 * The default value is true.
 */
allowPageDragging: boolean;
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
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.setViewMode(2,2);
DWObject.Viewer.cursor = "pointer";
DWObject.Viewer.allowPageDragging = false; //Disable drag&drop.
```

---

## background

**Syntax**

```typescript
/**
 * Return or set the background of the viewer.
 */
background: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.background = "rgb(255, 255, 255)";
```

**Usage notes**

Replace the previous `BackgroundColor` method. Now you can specify the backgournd by CSS which may be a single color or even an image. Read more on the [background shorthand CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/background).

---

## border

**Syntax**

```typescript
/**
 * Return or set the border of the viewer.
 */
border: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.border = "2px solid rgb(204, 204, 204)";
```

**Usage notes**

The default value is "1px solid rgb(204, 204, 204)". Now you can specify the border by CSS. Read more on the [border shorthand CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/border).

---

## cursor

**Syntax**

```typescript
/**
 * Return or set the shape of the cursor.
 */
cursor: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.cursor = "crosshair";
```

**Usage Notes**

The allowed values are:

| Value       | Description                                                                                                                                                 |
| :---------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `default`   | The shape is ![default]({{site.assets}}imgs/default.gif).                                                                                                   |
| `crosshair` | The shape is ![crosshair]({{site.assets}}imgs/crosshair.gif)(default setting), you can select one or multiple area(s) on the page.                          |
| `pointer`   | The shape is ![pointer]({{site.assets}}imgs/pointer.gif). If the displayed page is bigger than the viewer, the page can be moved.                           |
| `zoom-in`   | The shape is ![zoom-in]({{site.assets}}imgs/zoom-in.gif), supports click the page to zoom in. Only works if the view mode of the viewer is set to -1 by -1. |

If there are selected areas on the page, changing the `cursor` property will clear them.

---

## height

**Syntax**

```typescript
/**
 * Return or set the height of the viewer.
 */
height: number | string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.height = 350;
DWObject.Viewer.height = "350px";
DWObject.Viewer.height = "100%";
```

**Usage Notes**

If a number is assigned, it means that number of pixels (px). If a string is assigned, it is either a fixed size like "500px" or a dynamic size like "50%" which follows standard CSS rules.

When reading the property, the value is always in pixels no matter what value was set to it.

---

## idPostfix

**Syntax**

```typescript
/**
 * Return the postfix of the Ids of the elements in the viewer.
 */
readonly idPostfix: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
var myViewerIdPostfix = DWObject.Viewer.idPostfix;
```

---

## ifAutoScroll

**Syntax**

```typescript
/**
 * Return or set whether to scroll the viewer automatically when new pages are imported.
 * Default: true;
 */
ifAutoScroll: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.ifAutoScroll = false;
```

---

## innerBorder

**Syntax**

```typescript
/**
 * Return or set the inner border of the viewer.
 */
innerBorder: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.innerBorder = "1px solid rgb(204, 204, 204)";
```

**Usage notes**

The default value is null. You can specify the border by CSS. Read more on the [border shorthand CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/border).

---

## pageMargin

**Syntax**

```typescript
/**
 * Return or set the margin between images.
 */
pageMargin: number | string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.pageMargin = 10;
```

**Usage Notes**

The page margin is only effective when the view mode is not -1 \* -1 (in other words, [ `singlePageMode` ](#singlepagemode) is `false` ).

---

## selectedAreaBorderColor

**Syntax**

```typescript
/**
 * Set the border color of the selected area. Also applies to the selection box on the video opened by the method `showVideo`.
 */
selectedAreaBorderColor: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.selectedAreaBorderColor = "rgba(0, 0, 0, 1)";
```

**Usage notes**

The default value is "rgba(0, 0, 0, 1)".

---

## selectedPageBackground

**Syntax**

```typescript
/**
 * Set the selected page background color of the Thumbnail viewer.
 */
selectedPageBackground: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.selectedPageBackground = "rgb(255, 0, 0)";
```

**Usage notes**

The default value is "rgb(199, 222, 252)". You can specify the backgournd by CSS which may be a single color or even an image. Read more on the [background shorthand CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/background).

---

## selectedPageBorder

**Syntax**

```typescript
/**
 * Return or set the border style for selected page(s).
 */
selectedPageBorder: string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.selectedPageBorder = "3px solid rgb(125,162,206)";
```

**Usage Notes**

This API is only effective when the view mode is not -1 \* -1 (in other words, [ `singlePageMode` ](#singlepagemode) is `false` ).

The default value is "1px solid rgb(125, 162, 206)". Now you can specify the border by CSS. Read more on the [border shorthand CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/border).

---

## selectionRectAspectRatio

**Syntax**

```typescript
/**
 * Specify an aspect ratio to be used when selecting an rectangular area on a page.
 */
selectionRectAspectRatio: number | string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.selectionRectAspectRatio = 0.5;
```

**Usage Notes**

This API is only effective when drawing manually (it won't work if the selection is done with the API [`setSelectedAreas()`](#setselectedareas)).

---

## singlePageMode

**Syntax**

```typescript
/**
 * Set whether to use single page mode.
 */
singlePageMode: boolean;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
// Use single page mode in the main viewer
DWObject.Viewer.singlePageMode = true;
```

```javascript
// Use single page mode in the thumnail viewer
var objThumbnailViewer = DWObject.Viewer.createThumbnailViewer();
objThumbnailViewer.show();
DWObject.Viewer.singlePageMode = true;
```

**Usage notes**

The default value is `false`. If the thumbnail viewer is not shown, setting `singlePageMode` to `true` is equivalent to setting the view mode to -1 by -1. But if the thumbnail viewer is shown, `singlePageMode` will be changed to `true` automatically.

---

## width

**Syntax**

```typescript
/**
 * Return or set the width of the viewer.
 */
width: number | string;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.width = 270;
DWObject.Viewer.width = "270px";
DWObject.Viewer.width = "100%";
```

**Usage Notes**

If a number is assigned, it means that number of pixels (px). If a string is assigned, it is either a fixed size like "500px" or a dynamic size like "50%" which follows standard CSS rules.

When reading the property, the value is always in pixels no matter what value was set to it.

---

## zoom

**Syntax**

```typescript
/**
 * Return or set the zoom factor, and then the current page will be enlarged or reduced.
 */
zoom: number;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.zoom = 2.0;
```

**Usage Notes**

The zoom factor is only effective when the view mode is -1 \* -1. Allowed values is from 0.02 to 65.

---

## autoChangeIndex

**Syntax**

```typescript
/**
 * Set whether to make sure the first image in the viewer is always selected when scrolling through multiple images. The default value is false.
 */
autoChangeIndex: boolean;
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
<td align="center">v17.0+ </td>
<td align="center">v17.0+</td>
<td align="center">v17.0+</td>
<td align="center">v17.0+</td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.autoChangeIndex = true;
```

**Usage Notes**

When set to true, the index in the upper left corner of the viewer will be selected when scrolling.

---

## updateCheckboxStyle

**Syntax**

```typescript
/**
 * Update checkbox style
 * @argument checkboxSettings Settings for checkboxex.
 */
updateCheckboxStyle(checkboxSettings?: CheckboxSettings): void;

interface CheckboxSettings {
  visibility?: string; //"visible": hidden", default: "hidden" 
  width?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
  height?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
  background?: string; //default: "#ffffff"
  borderWidth?: number | string; //default: "2px", unit: px, percentage value not supported
  borderColor?: string; //default: "#000000"
  checkMarkColor?: string; //default: "#000000"
  checkMarkLineWidth?: number | string; //default: "2px", unit: px, percentage value not supported
  borderRadius?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%", relative to itself
  opacity?: number; //default:0.5, value range [0-1], value greater 1 defaults to 1
  left?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
  top?: number | string;  //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
  right?: number | string;  //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
  bottom?: number | string;  //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
  translateX?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to itself
  translateY?: number | string //default: "", number unit: px, string value: "10px"/"10%", relative to itself
}

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
<td align="center">not supported</td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
</tr>

</table>
</div>

---

## updatePageNumberStyle

**Syntax**

```typescript
/**
 * Update page number style
 * @argument pageNumberSettings Settings for page numbers.
 */
updatePageNumberStyle(pageNumberSettings?: PageNumberSettings): void;

interface pageNumberSettings {       
  visibility?: string; //"visible": hidden", default: "hidden" 
  width?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
  height?: number | string; //default: "24px", number unit: px, string value: "24px"/"10%", relative to parent container
  background?: string; //default:"#ffffff"            
  borderWidth?: number | string; //default: "1px", unit: px, percentage value not supported
  borderColor?: string; //default: "#a79898"
  borderRadius?: number | string; //default: "50%", number unit: px, string value: "10px"/"10%", relative to itself
  opacity?:number; //default: 0.5, value range [0-1], value greater 1 defaults to 1
  color?: string; //default: "#000000", supports #16 hexadecimal only
  fontFamily?: string; //default: "sans-serif"
  fontSize?: number | string; //default: 12, unit: px, percentage value not supported
  left?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
  top?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to parent container
  right?: number | string; //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
  bottom?: number | string; //default: 0, number unit: px, string value: "10px"/"10%", relative to parent container
  translateX?: number | string; //default: "", number unit: px, string value: "10px"/"10%", relative to itself
  translateY?: number | string //default: "", number unit: px, string value: "10px"/"10%", relative to itself
}

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
<td align="center">not supported</td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
<td align="center">v17.3+ </td>
</tr>

</table>
</div>

---

## selectionMode

**Syntax**

```typescript
/**
 * Return or set the selection mode used.
 */
selectionMode: Dynamsoft.DWT.EnumDWT_SelectionMode | number;
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
<td align="center">not supported</td>
<td align="center">v17.3+</td>
<td align="center">v17.3+</td>
<td align="center">v17.3+</td>
<td align="center">v17.3+</td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.setViewMode(2,2);
DWObject.Viewer.cursor = "pointer";
DWObject.Viewer.updateCheckboxStyle({
    visibility:"visible",
});
DWObject.Viewer.selectionMode = Dynamsoft.DWT.EnumDWT_SelectionMode.Multiple; // Multiple Selection
```

**Usage notes**

The default value is 0 (Single). Even if checkbox is used, only one image can be selected if the selection mode is set to 0 (Single).

---


## Events

### click

### contextmenu

### dblclick

### mousemove

### mousedown

### mouseup

### mouseout

### mouseover

### keydown

### keyup

**Syntax**

```typescript
/**
 * Built-in callbacks that are triggered for a certain mouse event or keyboard event on a page.
 * @param eventName Specify the event.
 * @param callback Specify the callback.
 * @argument dwtEvent The viewer-specific event object.
 * @argument domEvent The original mouse event object.
 */
on(
    eventName: string,
    callback: (event: ViewerEvent | KeyboardEvent, domEvent: MouseEvent) => void
): void;

interface ViewerEvent{
    // The index of the current page.
    index: number;
    //The x-coordinate of the upper-left corner of the page.
    imageX: number;
    //The y-coordinate of the upper-left corner of the page.
    imageY: number;
    // The x-coordinate of the browser page.
    pageX: number;
    // The y-coordinate of the browser page.
    pageY: number;
};
```

**Example**

```javascript
DWObject.Viewer.on("click", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("dblclick", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("contextmenu", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("mousemove", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("mousedown", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("mouseup", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("mouseout", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("mouseover", function (dwtEvent, domEvent) {
  console.log(dwtEvent, domEvent);
});

DWObject.Viewer.on("keydown", function (keyboardEvent) {
  console.log(keyboardEvent);
});

DWObject.Viewer.on("keyup", function (keyboardEvent) {
  console.log(keyboardEvent);
});
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
<td align="center">v16.2+ (partially supported) </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Usage notes**

The events `mouseout`, `mouseover`, `keydown` and `keyup` are only triggered on desktop browsers.
The events `click`, `dbclick`, `mousemove`, `pageAreaSelected`, and `pageAreaUnselected` are supported in ActiveX.

---

### pageAreaSelected

**Syntax**

```typescript
/**
 * This event is triggered when user selects an area (draws a rectangle) or move a selected area on the current page.
 * @argument index The index of the current page.
 * @argument rect Some attribute values of the selected area.
 */
on('pageAreaSelected',
    (index: number, rect: rect)=> void
): void;

interface rect{
    // The index of the selected area. The index is 0-based. This is useful when you have multiple selected areas on one page.
    areaIndex: number;
    // The x-coordinate of the upper-left corner of the area.
    x: number;
    // The y-coordinate of the upper-left corner of the area.
    y: number;
    // The width of the selected area.
    width: number;
    // The height of the selected area.
    height: number;
};
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.on("pageAreaSelected", function (sImageIndex, rect) {
  console.log(sImageIndex);
});

DWObject.Viewer.off("pageAreaSelected");
```

---

### pageAreaUnselected

**Syntax**

```typescript
/**
 * This event is triggered when selected area(s) get cleared (when the user clicks outside of the drawn rectangle).
 * @argument index The index of the current page.
 */
on('pageAreaUnselected',
    (index: number) => void
): void;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.on("pageAreaUnselected", function (sImageIndex) {
  console.log(
    "The selected areas on the page with index " +
      sImageIndex +
      " have been cleared"
  );
});

DWObject.Viewer.off("pageAreaUnselected");
```

---

### pageRendered

**Syntax**

```typescript
/**
 * This event is triggered when a page is rendered.
 * @argument index The index of the current page.
 */
on('pageRendered',
    (index: number) => void
): void;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.on("pageRendered", function (index) {
  console.log(index);
});
DWObject.Viewer.render(); //It will trigger the pageRendered event
```

---

### resize

**Syntax**

```typescript
/**
 * This event is triggered when width & height of the viewer has been changed.
 * @argument width The new width of the viewer.
 * @argument height The new height of the viewer.
 */
on('resize',
    (width: number, height: number) => void
): void;
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
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
<td align="center">v16.2+ </td>
</tr>

</table>
</div>

**Example**

```javascript
DWObject.Viewer.on("resize", function (width, height) {
  console.log(width, height);
});
DWObject.Viewer.width += 100;
```

---

<!--**### topPageChanged

**Syntax**

``` typescript
/**
 * This event is triggered when the top page currently displayed in the viewer changes.
 * @argument index The index of the current page.
 */
on('topPageChanged',
     (index: number) => void
): void;
```

**Example**

``` javascript
DWObject.Viewer.on("topPageChanged", function(index) {
    console.log(index);
});
```

**Usage Notes**

This event is only effective when the view mode is not -1 * -1 (in other words, [ `singlePageMode` ](#singlepagemode) is `false` ).
-->
