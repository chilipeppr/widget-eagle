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
| chilipeppr.load() URL | http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html |
| Edit URL              | http://ide.c9.io/chilipeppr/widget-eagle |
| Github URL            | http://github.com/chilipeppr/widget-eagle |
| Test URL              | https://preview.c9users.io/chilipeppr/widget-eagle/widget.html |

## Example Code for chilipeppr.load() Statement

You can use the code below as a starting point for instantiating this widget 
inside a workspace or from another widget. The key is that you need to load 
your widget inlined into a div so the DOM can parse your HTML, CSS, and 
Javascript. Then you use cprequire() to find your widget's Javascript and get 
back the instance of it.

```javascript
chilipeppr.load(
  "#myDivWidgetInsertedInto",
  "http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html",
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

  <table id="com-chilipeppr-elem-pubsubviewer-pub" class="table table-bordered table-striped">
      <thead>
          <tr>
              <th style="">Signal</th>
              <th style="">Description</th>
          </tr>
      </thead>
      <tbody>
<<<<<<< HEAD
      <tr valign="top"><td>/com-chilipeppr-widget-eagle/onAddGcode</td><td>This signal lets a 3rd party add-on inject its own Gcode into the 
            overall final Gcode for the Eagle BRD Widget. Here is an example of how to subscribe. <br><br><pre>
chilipeppr.subscribe("/com-chilipeppr-widget-eagle/addGcode", this, this.myOnAddGcode);
</pre>Then, your callback would look like this with 4 parameters receiving the variables 
            that the addGcode publish signal sends you. <br><br><pre>
onAddGcode : function(addGcodeCallback, gcodeParts, eagleWidget, helpDesc){ 
    console.log("Got onAddGcode:", arguments); 
    // this method calls back to the main Eagle widget to inject our Gcode 
    addGcodeCallback(1500, myOwnGcode ); 
} 
</pre>The 1500 in the example above is to attach a priority to where our Gcode will get positioned. 
            The base Gcode ends around line 900. The footer starts at line 2000. So putting our Gcode at 
            the end but before the footer means using 1500 should do fine. You can analyze the existing 
            Gcode by looking at parameter 2 gcodeParts to see if an index has already been used so you 
            don't clobber it. If you want to delete Gcode from gcodeParts you could do that as well and 
            the main widget will reflect the deletion. 
            </td></tr>    
=======
      <tr valign="top"><td>/com-chilipeppr-widget-template/onExampleGenerate</td><td>Example: Publish this signal when we go to generate gcode.</td></tr>    
>>>>>>> e373bef9fc32493cc462bb77d90b346b28ff5e96
      </tbody>
  </table>

## Subscribe

This widget/element subscribes to the following signals. These signals are owned by this widget/element. Other objects inside the ChiliPeppr environment can publish to these signals via the chilipeppr.publish(signal, data) method. 
To better understand how ChiliPeppr's publish() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

  <table id="com-chilipeppr-elem-pubsubviewer-sub" class="table table-bordered table-striped">
      <thead>
          <tr>
              <th style="">Signal</th>
              <th style="">Description</th>
          </tr>
      </thead>
      <tbody>
      <tr><td colspan="2">(No signals defined in this widget/element)</td></tr>    
      </tbody>
  </table>

## Foreign Publish

This widget/element publishes to the following signals that are owned by other objects. 
To better understand how ChiliPeppr's subscribe() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

  <table id="com-chilipeppr-elem-pubsubviewer-foreignpub" class="table table-bordered table-striped">
      <thead>
          <tr>
              <th style="">Signal</th>
              <th style="">Description</th>
          </tr>
      </thead>
      <tbody>
      <tr><td colspan="2">(No signals defined in this widget/element)</td></tr>    
      </tbody>
  </table>

## Foreign Subscribe

This widget/element publishes to the following signals that are owned by other objects.
To better understand how ChiliPeppr's publish() method works see amplify.js's documentation at http://amplifyjs.com/api/pubsub/

  <table id="com-chilipeppr-elem-pubsubviewer-foreignsub" class="table table-bordered table-striped">
      <thead>
          <tr>
              <th style="">Signal</th>
              <th style="">Description</th>
          </tr>
      </thead>
      <tbody>
<<<<<<< HEAD
      <tr valign="top"><td>/com-chilipeppr-widget-eagle/com-chilipeppr-elem-dragdrop/ondropped</td><td>We subscribe to this signal at a higher priority to intercept the signal, double check if it is an Eagle Brd file and if so, we do not let it propagate by returning false. That way the 3D Viewer, Gcode widget, or other widgets will not get Eagle Brd file drag/drop events because they will not know how to interpret them.</td></tr>    
=======
      <tr><td colspan="2">(No signals defined in this widget/element)</td></tr>    
>>>>>>> e373bef9fc32493cc462bb77d90b346b28ff5e96
      </tbody>
  </table>

## Methods / Properties

The table below shows, in order, the methods and properties inside the widget/element.

  <table id="com-chilipeppr-elem-methodsprops" class="table table-bordered table-striped">
      <thead>
          <tr>
              <th style="">Method / Property</th>
              <th>Type</th>
              <th style="">Description</th>
          </tr>
      </thead>
      <tbody>
<<<<<<< HEAD
      <tr valign="top"><td>id</td><td>string</td><td>"com-chilipeppr-widget-eagle"<br><br>The ID of the widget. You must define this and make it unique.</td></tr><tr valign="top"><td>name</td><td>string</td><td>"Widget / Eagle PCB v3"</td></tr><tr valign="top"><td>desc</td><td>string</td><td>"This widget lets you drag in an Eagle PCB \".brd\" file to mill."</td></tr><tr valign="top"><td>url</td><td>string</td><td>"http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html"</td></tr><tr valign="top"><td>fiddleurl</td><td>string</td><td>"http://ide.c9.io/chilipeppr/widget-eagle"</td></tr><tr valign="top"><td>githuburl</td><td>string</td><td>"http://github.com/chilipeppr/widget-eagle"</td></tr><tr valign="top"><td>testurl</td><td>string</td><td>"http://widget-eagle-chilipeppr.c9users.io/widget.html"</td></tr><tr valign="top"><td>publish</td><td>object</td><td>Please see docs above.<br><br>Define the publish signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>subscribe</td><td>object</td><td>Please see docs above.<br><br>Define the subscribe signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>foreignPublish</td><td>object</td><td>Please see docs above.<br><br>Document the foreign publish signals, i.e. signals owned by other widgets
or elements, that this widget/element publishes to.</td></tr><tr valign="top"><td>foreignSubscribe</td><td>object</td><td>Please see docs above.<br><br>Document the foreign subscribe signals, i.e. signals owned by other widgets
or elements, that this widget/element subscribes to.</td></tr><tr valign="top"><td>init</td><td>function</td><td>function (doMyOwnDragDrop) <br><br>All widgets should have an init method. It should be run by the
instantiating code like a workspace or a different widget.</td></tr><tr valign="top"><td>setupLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr valign="top"><td>populateLayerToggleDropdown</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>onChangeLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupFeedsDepths</td><td>function</td><td>function () </td></tr><tr valign="top"><td>calcPasses</td><td>function</td><td>function (el) </td></tr><tr valign="top"><td>activateWidget</td><td>function</td><td>function () <br><br>This method is called from the main workspace telling us the user
just activated us as a widget. This is not the same as load. Load
happens once. Activate happens many times if user closes then opens
us.</td></tr><tr valign="top"><td>unactivateWidget</td><td>function</td><td>function () </td></tr><tr valign="top"><td>init3d</td><td>function</td><td>function () <br><br>Try to get a reference to the 3D viewer.</td></tr><tr valign="top"><td>onInit3dSuccess</td><td>function</td><td>function () </td></tr><tr valign="top"><td>obj3d</td><td>object</td><td></td></tr><tr valign="top"><td>obj3dmeta</td><td>object</td><td></td></tr><tr valign="top"><td>userCallbackForGet3dObj</td><td>object</td><td></td></tr><tr valign="top"><td>get3dObj</td><td>function</td><td>function (callback) </td></tr><tr valign="top"><td>get3dObjCallback</td><td>function</td><td>function (data, meta) </td></tr><tr valign="top"><td>is3dViewerReady</td><td>boolean</td><td></td></tr><tr valign="top"><td>clear3dViewer</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearEagleBrd</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearEagleBrdStep2</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupGcodeTab</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sendGcodeToWorkspace</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupDragDrop</td><td>function</td><td>function () </td></tr><tr valign="top"><td>eagle</td><td>object</td><td></td></tr><tr valign="top"><td>open</td><td>function</td><td>function (data, info) </td></tr><tr valign="top"><td>draw3d</td><td>function</td><td>function (callback) <br><br>We need the 3D viewer to be ready to go for us to generate our 3D view,
so do a little bit of a wait sequence here where we try 3 times to
grab the 3D viewer object and then we can render our board.
Alternately, we could render our board and then inject into the 3D
viewer later. Not sure why I didn't do it that way initially.</td></tr><tr valign="top"><td>colorSignal</td><td>number</td><td></td></tr><tr valign="top"><td>colorSmd</td><td>number</td><td></td></tr><tr valign="top"><td>colorSignalBottom</td><td>number</td><td></td></tr><tr valign="top"><td>colorSmdBottom</td><td>number</td><td></td></tr><tr valign="top"><td>colorVia</td><td>number</td><td></td></tr><tr valign="top"><td>colorPad</td><td>number</td><td></td></tr><tr valign="top"><td>colorMill</td><td>number</td><td></td></tr><tr valign="top"><td>colorHole</td><td>number</td><td></td></tr><tr valign="top"><td>colorsDrop</td><td>object</td><td></td></tr><tr valign="top"><td>colorDimension</td><td>number</td><td></td></tr><tr valign="top"><td>opacitySignal</td><td>number</td><td></td></tr><tr valign="top"><td>opacityDimension</td><td>number</td><td></td></tr><tr valign="top"><td>opacityVia</td><td>number</td><td></td></tr><tr valign="top"><td>opacityPad</td><td>number</td><td></td></tr><tr valign="top"><td>endmillSize</td><td>number</td><td></td></tr><tr valign="top"><td>actualEndmill</td><td>number</td><td></td></tr><tr valign="top"><td>inflateMillPathBy</td><td>object</td><td></td></tr><tr valign="top"><td>paths</td><td>object</td><td></td></tr><tr valign="top"><td>pathsUnion</td><td>object</td><td></td></tr><tr valign="top"><td>pathsUnionHoles</td><td>object</td><td></td></tr><tr valign="top"><td>threeDimensions</td><td>object</td><td></td></tr><tr valign="top"><td>activeLayer</td><td>string</td><td>"Top"</td></tr><tr valign="top"><td>clipperDimensions</td><td>object</td><td></td></tr><tr valign="top"><td>onDraw3dReady</td><td>function</td><td>function () <br><br>This is a key method that will actually start the traversal of the
entire Eagle BRD and generate Three.js objects for each pad/smd/via/wire, etc.
Then it will generate Clipper Paths which are just 2d xy values in the
format that the Clipper library wants so we can do unions and diffs
which is important to generate the isolation paths as well as deal with
polygons that may be on the board representing signal planes like a 
GND plane.</td></tr><tr valign="top"><td>onDraw3dReadyAfter</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearanceHeight</td><td>number</td><td></td></tr><tr valign="top"><td>depthOfSignalMilling</td><td>number</td><td></td></tr><tr valign="top"><td>feedRatePlunge</td><td>number</td><td></td></tr><tr valign="top"><td>feedRateSignals</td><td>number</td><td></td></tr><tr valign="top"><td>feedRateDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>drillFeedrate</td><td>number</td><td></td></tr><tr valign="top"><td>drillMaxDiameter</td><td>number</td><td></td></tr><tr valign="top"><td>drillDepth</td><td>number</td><td></td></tr><tr valign="top"><td>depthOfDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>millDiameter</td><td>number</td><td></td></tr><tr valign="top"><td>stepDownDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>stepDownPasses</td><td>number</td><td></td></tr><tr valign="top"><td>generateGcodeHole</td><td>function</td><td>function (diameter, x, y)</td></tr><tr valign="top"><td>exportGcodeHeader</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMilling</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMarkVias</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMarkPads</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeDrillVias</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeDrillPads</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeDimensions</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeFooter</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcode</td><td>function</td><td>function () </td></tr><tr valign="top"><td>gcodeParts</td><td>object</td><td></td></tr><tr valign="top"><td>addGcode</td><td>function</td><td>function (count, gcode)</td></tr><tr valign="top"><td>getGcode</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupAdvancedInflateByUI</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onRefresh</td><td>function</td><td>function (event, callback) </td></tr><tr valign="top"><td>threePathEndMill</td><td>object</td><td></td></tr><tr valign="top"><td>onRefresh2nd</td><td>function</td><td>function (event, callback) </td></tr><tr valign="top"><td>getInflatePathWithConstraint</td><td>function</td><td>function (paths, inflateBy, constraints) </td></tr><tr valign="top"><td>raycaster</td><td>object</td><td></td></tr><tr valign="top"><td>projector</td><td>object</td><td></td></tr><tr valign="top"><td>arrowHelper</td><td>object</td><td></td></tr><tr valign="top"><td>intersectObjects</td><td>object</td><td></td></tr><tr valign="top"><td>renderArea</td><td>object</td><td></td></tr><tr valign="top"><td>infoArea</td><td>object</td><td></td></tr><tr valign="top"><td>infoSignalArea</td><td>object</td><td></td></tr><tr valign="top"><td>lastIntersect</td><td>object</td><td></td></tr><tr valign="top"><td>hidePopupsElem</td><td>object</td><td></td></tr><tr valign="top"><td>setupMouseOver</td><td>function</td><td>function () </td></tr><tr valign="top"><td>reactivateMouseMove</td><td>function</td><td>function () </td></tr><tr valign="top"><td>deactivateMouseMove</td><td>function</td><td>function () </td></tr><tr valign="top"><td>hidePopups</td><td>function</td><td>function () </td></tr><tr valign="top"><td>lastIntersectOtherMaterials</td><td>object</td><td></td></tr><tr valign="top"><td>onMouseOver</td><td>function</td><td>function (event) </td></tr><tr valign="top"><td>getXorOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getIntersectionOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getDiffOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getAllPathsAsOuterOrientation</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>getUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>drawUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>drawClipperPaths</td><td>function</td><td>function (paths, color, opacity, z, zstep, isClosed, isAddDirHelper) </td></tr><tr valign="top"><td>createClipperPathsAsMesh</td><td>function</td><td>function (paths, color, opacity, holePath) </td></tr><tr valign="top"><td>getInflatePath</td><td>function</td><td>function (paths, delta, joinType) </td></tr><tr valign="top"><td>createThermalCutoutsFromSmd</td><td>function</td><td>function (smd, poly, myInflateBy) </td></tr><tr valign="top"><td>sortObjByKey</td><td>function</td><td>function (obj)</td></tr><tr valign="top"><td>clipperDimension</td><td>object</td><td></td></tr><tr valign="top"><td>getDimensionWires</td><td>function</td><td>function () </td></tr><tr valign="top"><td>draw3dDimension</td><td>function</td><td>function (endmillSize) </td></tr><tr valign="top"><td>addStrokeCapsToLine</td><td>function</td><td>function (x1, y1, x2, y2, width, capType) </td></tr><tr valign="top"><td>clipperBySignalKey</td><td>object</td><td></td></tr><tr valign="top"><td>clipperBySignalKeyItem</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSignalWires</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSignalPolys</td><td>object</td><td></td></tr><tr valign="top"><td>draw3dVias</td><td>function</td><td>function (layersName) </td></tr><tr valign="top"><td>draw3dSignalWires</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>draw3dSignalPolygons</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>clipperElements</td><td>object</td><td></td></tr><tr valign="top"><td>clipperPads</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSmds</td><td>object</td><td></td></tr><tr valign="top"><td>clipperVias</td><td>object</td><td></td></tr><tr valign="top"><td>drillPads</td><td>object</td><td></td></tr><tr valign="top"><td>drillVias</td><td>object</td><td></td></tr><tr valign="top"><td>draw3dElements</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>rotObjectMatrix</td><td>object</td><td></td></tr><tr valign="top"><td>rotateAroundObjectAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr valign="top"><td>rotWorldMatrix</td><td>object</td><td></td></tr><tr valign="top"><td>rotateAroundWorldAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr valign="top"><td>drawCircle</td><td>function</td><td>function (x, y, radius, color)</td></tr><tr valign="top"><td>drawSphere</td><td>function</td><td>function (x, y, radius, color)</td></tr><tr valign="top"><td>drawSquare</td><td>function</td><td>function (x1, y1, x2, y2) </td></tr><tr valign="top"><td>mySceneGroup</td><td>object</td><td></td></tr><tr valign="top"><td>sceneReAddMySceneGroup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sceneRemoveMySceneGroup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sceneAdd</td><td>function</td><td>function (obj) </td></tr><tr valign="top"><td>sceneRemove</td><td>function</td><td>function (obj) </td></tr><tr valign="top"><td>draw</td><td>function</td><td>function (e) </td></tr><tr valign="top"><td>onDropped</td><td>function</td><td>function (data, info) </td></tr><tr valign="top"><td>onDragOver</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onDragLeave</td><td>function</td><td>function () </td></tr><tr valign="top"><td>isVidLoaded</td><td>boolean</td><td></td></tr><tr valign="top"><td>lazyLoadTutorial</td><td>function</td><td>function () </td></tr><tr valign="top"><td>options</td><td>object</td><td></td></tr><tr valign="top"><td>setupUiFromLocalStorage</td><td>function</td><td>function () </td></tr><tr valign="top"><td>saveOptionsLocalStorage</td><td>function</td><td>function () </td></tr><tr valign="top"><td>showBody</td><td>function</td><td>function (evt) </td></tr><tr valign="top"><td>hideBody</td><td>function</td><td>function (evt) </td></tr><tr valign="top"><td>btnSetup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>statusEl</td><td>object</td><td></td></tr><tr valign="top"><td>status</td><td>function</td><td>function (txt) </td></tr><tr valign="top"><td>forkSetup</td><td>function</td><td>function () </td></tr>
=======
      <tr valign="top"><td>id</td><td>string</td><td>"com-chilipeppr-widget-template"<br><br>The ID of the widget. You must define this and make it unique.</td></tr><tr valign="top"><td>name</td><td>string</td><td>"Widget / Template"</td></tr><tr valign="top"><td>desc</td><td>string</td><td>"This example widget gives you a framework for creating your own widget. Please change this description once you fork this template and create your own widget. Make sure to run runme.js every time you are done editing your code so you can regenerate your README.md file, regenerate your auto-generated-widget.html, and automatically push your changes to Github."</td></tr><tr valign="top"><td>url</td><td>string</td><td>"http://raw.githubusercontent.com/chilipeppr/widget-template/master/auto-generated-widget.html"</td></tr><tr valign="top"><td>fiddleurl</td><td>string</td><td>"http://ide.c9.io/chilipeppr/widget-template"</td></tr><tr valign="top"><td>githuburl</td><td>string</td><td>"http://github.com/chilipeppr/widget-template"</td></tr><tr valign="top"><td>testurl</td><td>string</td><td>"http://widget-template-chilipeppr.c9users.io/widget.html"</td></tr><tr valign="top"><td>publish</td><td>object</td><td>Please see docs above.<br><br>Define the publish signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>subscribe</td><td>object</td><td>Please see docs above.<br><br>Define the subscribe signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>foreignPublish</td><td>object</td><td>Please see docs above.<br><br>Document the foreign publish signals, i.e. signals owned by other widgets
or elements, that this widget/element publishes to.</td></tr><tr valign="top"><td>foreignSubscribe</td><td>object</td><td>Please see docs above.<br><br>Document the foreign subscribe signals, i.e. signals owned by other widgets
or elements, that this widget/element subscribes to.</td></tr><tr valign="top"><td>init</td><td>function</td><td>function () <br><br>All widgets should have an init method. It should be run by the
instantiating code like a workspace or a different widget.</td></tr><tr valign="top"><td>btnSetup</td><td>function</td><td>function () <br><br>Call this method from init to setup all the buttons when this widget
is first loaded. This basically attaches click events to your 
buttons. It also turns on all the bootstrap popovers by scanning
the entire DOM of the widget.</td></tr><tr valign="top"><td>onHelloBtnClick</td><td>function</td><td>function (evt) <br><br>onHelloBtnClick is an example of a button click event callback</td></tr><tr valign="top"><td>options</td><td>object</td><td>User options are available in this property for reference by your
methods. If any change is made on these options, please call
saveOptionsLocalStorage()</td></tr><tr valign="top"><td>setupUiFromLocalStorage</td><td>function</td><td>function () <br><br>Call this method on init to setup the UI by reading the user's
stored settings from localStorage and then adjust the UI to reflect
what the user wants.</td></tr><tr valign="top"><td>saveOptionsLocalStorage</td><td>function</td><td>function () <br><br>When a user changes a value that is stored as an option setting, you
should call this method immediately so that on next load the value
is correctly set.</td></tr><tr valign="top"><td>showBody</td><td>function</td><td>function (evt) <br><br>Show the body of the panel.
<br><br><b>evt</b> ({jquery_event})  - If you pass the event parameter in, we 
know it was clicked by the user and thus we store it for the next 
load so we can reset the user's preference. If you don't pass this 
value in we don't store the preference because it was likely code 
that sent in the param.</td></tr><tr valign="top"><td>hideBody</td><td>function</td><td>function (evt) <br><br>Hide the body of the panel.
<br><br><b>evt</b> ({jquery_event})  - If you pass the event parameter in, we 
know it was clicked by the user and thus we store it for the next 
load so we can reset the user's preference. If you don't pass this 
value in we don't store the preference because it was likely code 
that sent in the param.</td></tr><tr valign="top"><td>forkSetup</td><td>function</td><td>function () <br><br>This method loads the pubsubviewer widget which attaches to our 
upper right corner triangle menu and generates 3 menu items like
Pubsub Viewer, View Standalone, and Fork Widget. It also enables
the modal dialog that shows the documentation for this widget.<br><br>By using chilipeppr.load() we can ensure that the pubsubviewer widget
is only loaded and inlined once into the final ChiliPeppr workspace.
We are given back a reference to the instantiated singleton so its
not instantiated more than once. Then we call it's attachTo method
which creates the full pulldown menu for us and attaches the click
events.</td></tr>
>>>>>>> e373bef9fc32493cc462bb77d90b346b28ff5e96
      </tbody>
  </table>


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

