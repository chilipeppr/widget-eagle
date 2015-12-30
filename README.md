# com-chilipeppr-widget-eagle
This widget lets you drag in an Eagle PCB ".brd" file to mill.

![alt text](screenshot.png "Screenshot")

## ChiliPeppr Widget / Eagle PCB v3

All ChiliPeppr widgets/elements are defined using cpdefine() which is a method
that mimics require.js. Each defined object must have a unique ID so it does
not conflict with other ChiliPeppr widgets.

| Item                  | Value           |
| -------------         | ------------- | 
| ID                    | com-chilipeppr-widget-eagle |
| Name                  | Widget / Eagle PCB v3 |
| Description           | This widget lets you drag in an Eagle PCB ".brd" file to mill. |
| chilipeppr.load() URL | http://raw.githubusercontent.com/raykholo/widget-eagle/master/auto-generated-widget.html |
| Edit URL              | http://ide.c9.io/raykholo/widget-eagle |
| Github URL            | http://github.com/raykholo/widget-eagle |
| Test URL              | https://preview.c9users.io/raykholo/widget-eagle/widget.html |

## Example Code for chilipeppr.load() Statement

You can use the code below as a starting point for instantiating this widget 
inside a workspace or from another widget. The key is that you need to load 
your widget inlined into a div so the DOM can parse your HTML, CSS, and 
Javascript. Then you use cprequire() to find your widget's Javascript and get 
back the instance of it.

```javascript
chilipeppr.load(
  "#myDivWidgetInsertedInto",
  "http://raw.githubusercontent.com/raykholo/widget-eagle/master/auto-generated-widget.html",
  function() {
    // Callback after widget loaded into #myDivWidgetInsertedInto
    cprequire(
      ["inline:com-chilipeppr-widget-eagle"], // the id you gave your widget
      function(mywidget) {
        // Callback that is passed reference to your newly loaded widget
        console.log("My widget just got loaded.", mywidget);
        mywidget.init();
      }
    );
  }
);

```

## Publish

This widget/element publishes the following signals. These signals are owned by this widget/element and are published to all objects inside the ChiliPeppr environment that listen to them via the 
chilipeppr.subscribe(signal, callback) method. 
To better understand how ChiliPeppr's subscribe() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

| Signal | Description |
| ------ | ----------- |
| /com-chilipeppr-widget-eagle/onAddGcode | This signal lets a 3rd party add-on inject its own Gcode into the             overall final Gcode for the Eagle BRD Widget. Here is an example of how to subscribe.                         chilipeppr.subscribe("/com-chilipeppr-widget-eagle/addGcode", this, this.myOnAddGcode);                         Then, your callback would look like this with 4 parameters receiving the variables             that the addGcode publish signal sends you.                         onAddGcode : function(addGcodeCallback, gcodeParts, eagleWidget, helpDesc){                 console.log("Got onAddGcode:", arguments);                 // this method calls back to the main Eagle widget to inject our Gcode                 addGcodeCallback(1500, myOwnGcode );             }                         The 1500 in the example above is to attach a priority to where our Gcode will get positioned.             The base Gcode ends around line 900. The footer starts at line 2000. So putting our Gcode at             the end but before the footer means using 1500 should do fine. You can analyze the existing             Gcode by looking at parameter 2 gcodeParts to see if an index has already been used so you             don't clobber it. If you want to delete Gcode from gcodeParts you could do that as well and             the main widget will reflect the deletion.              |

## Subscribe

This widget/element subscribes to the following signals. These signals are owned by this widget/element. Other objects inside the ChiliPeppr environment can publish to these signals via the chilipeppr.publish(signal, data) method. 
To better understand how ChiliPeppr's publish() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

| Signal | Description |
| ------ | ----------- |
| (No signals defined in this widget/element) |

## Foreign Publish

This widget/element publishes to the following signals that are owned by other objects. 
To better understand how ChiliPeppr's subscribe() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

| Signal | Description |
| ------ | ----------- |
| (No signals defined in this widget/element) |

## Foreign Subscribe

This widget/element publishes to the following signals that are owned by other objects.
To better understand how ChiliPeppr's publish() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

| Signal | Description |
| ------ | ----------- |
| /com-chilipeppr-widget-eagle/com-chilipeppr-elem-dragdrop/ondropped | We subscribe to this signal at a higher priority to intercept the signal, double check if it is an Eagle Brd file and if so, we do not let it propagate by returning false. That way the 3D Viewer, Gcode widget, or other widgets will not get Eagle Brd file drag/drop events because they will not know how to interpret them. |

## Methods / Properties

The table below shows, in order, the methods and properties inside the widget/element.

| Item                  | Type          | Description |
| -------------         | ------------- | ----------- |
| id | string | "com-chilipeppr-widget-eagle"<br><br>The ID of the widget. You must define this and make it unique. |
| name | string | "Widget / Eagle PCB v3" |
| desc | string | "This widget lets you drag in an Eagle PCB \".brd\" file to mill." |
| url | string | "http://raw.githubusercontent.com/raykholo/widget-eagle/master/auto-generated-widget.html" |
| fiddleurl | string | "http://ide.c9.io/raykholo/widget-eagle" |
| githuburl | string | "http://github.com/raykholo/widget-eagle" |
| testurl | string | "http://widget-eagle-raykholo.c9users.io/widget.html" |
| publish | object | Please see docs above.<br><br>Define the publish signals that this widget/element owns or defines so thatother widgets know how to subscribe to them and what they do. |
| subscribe | object | Please see docs above.<br><br>Define the subscribe signals that this widget/element owns or defines so thatother widgets know how to subscribe to them and what they do. |
| foreignPublish | object | Please see docs above.<br><br>Document the foreign publish signals, i.e. signals owned by other widgetsor elements, that this widget/element publishes to. |
| foreignSubscribe | object | Please see docs above.<br><br>Document the foreign subscribe signals, i.e. signals owned by other widgetsor elements, that this widget/element subscribes to. |
| init | function | function (doMyOwnDragDrop) <br><br>All widgets should have an init method. It should be run by theinstantiating code like a workspace or a different widget. |
| setupLayerToggleDropdown | function | function ()  |
| populateLayerToggleDropdown | function | function () |
| onChangeLayerToggleDropdown | function | function ()  |
| setupFeedsDepths | function | function ()  |
| calcPasses | function | function (el)  |
| activateWidget | function | function () <br><br>This method is called from the main workspace telling us the userjust activated us as a widget. This is not the same as load. Loadhappens once. Activate happens many times if user closes then opensus. |
| unactivateWidget | function | function ()  |
| init3d | function | function () <br><br>Try to get a reference to the 3D viewer. |
| onInit3dSuccess | function | function ()  |
| obj3d | object |  |
| obj3dmeta | object |  |
| userCallbackForGet3dObj | object |  |
| get3dObj | function | function (callback)  |
| get3dObjCallback | function | function (data, meta)  |
| is3dViewerReady | boolean |  |
| clear3dViewer | function | function ()  |
| clearEagleBrd | function | function ()  |
| clearEagleBrdStep2 | function | function ()  |
| setupGcodeTab | function | function ()  |
| sendGcodeToWorkspace | function | function ()  |
| setupDragDrop | function | function ()  |
| eagle | object |  |
| open | function | function (data, info)  |
| draw3d | function | function (callback) <br><br>We need the 3D viewer to be ready to go for us to generate our 3D view,so do a little bit of a wait sequence here where we try 3 times tograb the 3D viewer object and then we can render our board.Alternately, we could render our board and then inject into the 3Dviewer later. Not sure why I didn't do it that way initially. |
| colorSignal | number |  |
| colorSmd | number |  |
| colorSignalBottom | number |  |
| colorSmdBottom | number |  |
| colorVia | number |  |
| colorPad | number |  |
| colorMill | number |  |
| colorHole | number |  |
| colorsDrop | object |  |
| colorDimension | number |  |
| opacitySignal | number |  |
| opacityDimension | number |  |
| opacityVia | number |  |
| opacityPad | number |  |
| endmillSize | number |  |
| actualEndmill | number |  |
| inflateMillPathBy | object |  |
| paths | object |  |
| pathsUnion | object |  |
| pathsUnionHoles | object |  |
| threeDimensions | object |  |
| activeLayer | string | "Top" |
| clipperDimensions | object |  |
| onDraw3dReady | function | function () <br><br>This is a key method that will actually start the traversal of theentire Eagle BRD and generate Three.js objects for each pad/smd/via/wire, etc.Then it will generate Clipper Paths which are just 2d xy values in theformat that the Clipper library wants so we can do unions and diffswhich is important to generate the isolation paths as well as deal withpolygons that may be on the board representing signal planes like a GND plane. |
| onDraw3dReadyAfter | function | function ()  |
| clearanceHeight | number |  |
| depthOfSignalMilling | number |  |
| feedRatePlunge | number |  |
| feedRateSignals | number |  |
| feedRateDimensions | number |  |
| drillFeedrate | number |  |
| drillMaxDiameter | number |  |
| drillDepth | number |  |
| depthOfDimensions | number |  |
| millDiameter | number |  |
| stepDownDimensions | number |  |
| stepDownPasses | number |  |
| generateGcodeHole | function | function (diameter, x, y) |
| exportGcodeHeader | function | function () |
| exportGcodeMilling | function | function () |
| exportGcodeMarkVias | function | function () |
| exportGcodeMarkPads | function | function () |
| exportGcodeDrillVias | function | function () |
| exportGcodeDrillPads | function | function () |
| exportGcodeDimensions | function | function () |
| exportGcodeFooter | function | function () |
| exportGcode | function | function ()  |
| addGcode | function | function (count, gcode) |
| getGcode | function | function ()  |
| setupAdvancedInflateByUI | function | function ()  |
| onRefresh | function | function (event, callback)  |
| threePathEndMill | object |  |
| onRefresh2nd | function | function (event, callback)  |
| getInflatePathWithConstraint | function | function (paths, inflateBy, constraints)  |
| raycaster | object |  |
| projector | object |  |
| arrowHelper | object |  |
| intersectObjects | object |  |
| renderArea | object |  |
| infoArea | object |  |
| infoSignalArea | object |  |
| lastIntersect | object |  |
| hidePopupsElem | object |  |
| setupMouseOver | function | function ()  |
| reactivateMouseMove | function | function ()  |
| deactivateMouseMove | function | function ()  |
| hidePopups | function | function ()  |
| lastIntersectOtherMaterials | object |  |
| onMouseOver | function | function (event)  |
| getXorOfClipperPaths | function | function (subj_paths, clip_paths)  |
| getIntersectionOfClipperPaths | function | function (subj_paths, clip_paths)  |
| getDiffOfClipperPaths | function | function (subj_paths, clip_paths)  |
| getAllPathsAsOuterOrientation | function | function (subj_paths)  |
| getUnionOfClipperPaths | function | function (subj_paths)  |
| drawUnionOfClipperPaths | function | function (subj_paths)  |
| drawClipperPaths | function | function (paths, color, opacity, z, zstep, isClosed, isAddDirHelper)  |
| createClipperPathsAsMesh | function | function (paths, color, opacity, holePath)  |
| getInflatePath | function | function (paths, delta, joinType)  |
| createThermalCutoutsFromSmd | function | function (smd, poly, myInflateBy)  |
| sortObjByKey | function | function (obj) |
| clipperDimension | object |  |
| getDimensionWires | function | function ()  |
| draw3dDimension | function | function (endmillSize)  |
| addStrokeCapsToLine | function | function (x1, y1, x2, y2, width, capType)  |
| clipperBySignalKey | object |  |
| clipperBySignalKeyItem | object |  |
| clipperSignalWires | object |  |
| clipperSignalPolys | object |  |
| draw3dVias | function | function (layersName)  |
| draw3dSignalWires | function | function (layer)  |
| draw3dSignalPolygons | function | function (layer)  |
| clipperElements | object |  |
| clipperPads | object |  |
| clipperSmds | object |  |
| clipperVias | object |  |
| drillPads | object |  |
| drillVias | object |  |
| draw3dElements | function | function (layer)  |
| rotObjectMatrix | object |  |
| rotateAroundObjectAxis | function | function (object, axis, radians)  |
| rotWorldMatrix | object |  |
| rotateAroundWorldAxis | function | function (object, axis, radians)  |
| drawCircle | function | function (x, y, radius, color) |
| drawSphere | function | function (x, y, radius, color) |
| drawSquare | function | function (x1, y1, x2, y2)  |
| mySceneGroup | object |  |
| sceneReAddMySceneGroup | function | function ()  |
| sceneRemoveMySceneGroup | function | function ()  |
| sceneAdd | function | function (obj)  |
| sceneRemove | function | function (obj)  |
| draw | function | function (e)  |
| onDropped | function | function (data, info)  |
| onDragOver | function | function ()  |
| onDragLeave | function | function ()  |
| isVidLoaded | boolean |  |
| lazyLoadTutorial | function | function ()  |
| options | object |  |
| setupUiFromLocalStorage | function | function ()  |
| saveOptionsLocalStorage | function | function ()  |
| showBody | function | function (evt)  |
| hideBody | function | function (evt)  |
| btnSetup | function | function ()  |
| statusEl | object |  |
| status | function | function (txt)  |
| forkSetup | function | function ()  |


## About ChiliPeppr

[ChiliPeppr](http://chilipeppr.com) is a hardware fiddle, meaning it is a 
website that lets you easily
create a workspace to fiddle with your hardware from software. ChiliPeppr provides
a [Serial Port JSON Server](https://github.com/johnlauer/serial-port-json-server) 
that you run locally on your computer, or remotely on another computer, to connect to 
the serial port of your hardware like an Arduino or other microcontroller.

You then create a workspace at ChiliPeppr.com that connects to your hardware 
by starting from scratch or forking somebody else's
workspace that is close to what you are after. Then you write widgets in
Javascript that interact with your hardware by forking the base template 
widget or forking another widget that
is similar to what you are trying to build.

ChiliPeppr is massively capable such that the workspaces for 
[TinyG](http://chilipeppr.com/tinyg) and [Grbl](http://chilipeppr.com/grbl) CNC 
controllers have become full-fledged CNC machine management software used by
tens of thousands.

ChiliPeppr has inspired many people in the hardware/software world to use the
browser and Javascript as the foundation for interacting with hardware. The
Arduino team in Italy caught wind of ChiliPeppr and now
ChiliPeppr's Serial Port JSON Server is the basis for the 
[Arduino's new web IDE](https://create.arduino.cc/). If the Arduino team is excited about building on top
of ChiliPeppr, what
will you build on top of it?



