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
      <tr><td>/com-chilipeppr-widget-eagle/onAddGcode</td><td>This signal lets a 3rd party add-on inject its own Gcode into the             overall final Gcode for the Eagle BRD Widget. Here is an example of how to subscribe.             <pre>
chilipeppr.subscribe("/com-chilipeppr-widget-eagle/addGcode", this, this.myOnAddGcode);
 </pre>                        Then, your callback would look like this with 4 parameters receiving the variables             that the addGcode publish signal sends you.             <pre>
onAddGcode : function(addGcodeCallback, gcodeParts, eagleWidget, helpDesc){ 
    console.log("Got onAddGcode:", arguments); 
    // this method calls back to the main Eagle widget to inject our Gcode 
    addGcodeCallback(1500, myOwnGcode ); 
} 
</pre>            The 1500 in the example above is to attach a priority to where our Gcode will get positioned.             The base Gcode ends around line 900. The footer starts at line 2000. So putting our Gcode at             the end but before the footer means using 1500 should do fine. You can analyze the existing             Gcode by looking at parameter 2 gcodeParts to see if an index has already been used so you             don't clobber it. If you want to delete Gcode from gcodeParts you could do that as well and             the main widget will reflect the deletion.             </td></tr>    
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
      
      <tr><td>/com-chilipeppr-widget-eagle/com-chilipeppr-elem-dragdrop/ondropped</td><td>We subscribe to this signal at a higher priority to intercept the signal, double check if it is an Eagle Brd file and if so, we do not let it propagate by returning false. That way the 3D Viewer, Gcode widget, or other widgets will not get Eagle Brd file drag/drop events because they will not know how to interpret them.</td></tr>    
      
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
      <tr><td>id</td><td>string</td><td>"com-chilipeppr-widget-eagle"<br><br>The ID of the widget. You must define this and make it unique.</td></tr><tr><td>name</td><td>string</td><td>"Widget / Eagle PCB v3"</td></tr><tr><td>desc</td><td>string</td><td>"This widget lets you drag in an Eagle PCB \".brd\" file to mill."</td></tr><tr><td>url</td><td>string</td><td>"http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html"</td></tr><tr><td>fiddleurl</td><td>string</td><td>"http://ide.c9.io/chilipeppr/widget-eagle"</td></tr><tr><td>githuburl</td><td>string</td><td>"http://github.com/chilipeppr/widget-eagle"</td></tr><tr><td>testurl</td><td>string</td><td>"http://widget-eagle-chilipeppr.c9users.io/widget.html"</td></tr><tr><td>publish</td><td>object</td><td>Please see docs above.<br><br>Define the publish signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr><td>subscribe</td><td>object</td><td>Please see docs above.<br><br>Define the subscribe signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr><td>foreignPublish</td><td>object</td><td>Please see docs above.<br><br>Document the foreign publish signals, i.e. signals owned by other widgets
or elements, that this widget/element publishes to.</td></tr><tr><td>foreignSubscribe</td><td>object</td><td>Please see docs above.<br><br>Document the foreign subscribe signals, i.e. signals owned by other widgets
or elements, that this widget/element subscribes to.</td></tr><tr><td>init</td><td>function</td><td>function (doMyOwnDragDrop) <br><br>All widgets should have an init method. It should be run by the
instantiating code like a workspace or a different widget.</td></tr><tr><td>setupLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr><td>populateLayerToggleDropdown</td><td>function</td><td>function ()</td></tr><tr><td>onChangeLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr><td>setupFeedsDepths</td><td>function</td><td>function () </td></tr><tr><td>calcPasses</td><td>function</td><td>function (el) </td></tr><tr><td>activateWidget</td><td>function</td><td>function () <br><br>This method is called from the main workspace telling us the user
just activated us as a widget. This is not the same as load. Load
happens once. Activate happens many times if user closes then opens
us.</td></tr><tr><td>unactivateWidget</td><td>function</td><td>function () </td></tr><tr><td>init3d</td><td>function</td><td>function () <br><br>Try to get a reference to the 3D viewer.</td></tr><tr><td>onInit3dSuccess</td><td>function</td><td>function () </td></tr><tr><td>obj3d</td><td>object</td><td></td></tr><tr><td>obj3dmeta</td><td>object</td><td></td></tr><tr><td>userCallbackForGet3dObj</td><td>object</td><td></td></tr><tr><td>get3dObj</td><td>function</td><td>function (callback) </td></tr><tr><td>get3dObjCallback</td><td>function</td><td>function (data, meta) </td></tr><tr><td>is3dViewerReady</td><td>boolean</td><td></td></tr><tr><td>clear3dViewer</td><td>function</td><td>function () </td></tr><tr><td>clearEagleBrd</td><td>function</td><td>function () </td></tr><tr><td>clearEagleBrdStep2</td><td>function</td><td>function () </td></tr><tr><td>setupGcodeTab</td><td>function</td><td>function () </td></tr><tr><td>sendGcodeToWorkspace</td><td>function</td><td>function () </td></tr><tr><td>setupDragDrop</td><td>function</td><td>function () </td></tr><tr><td>eagle</td><td>object</td><td></td></tr><tr><td>open</td><td>function</td><td>function (data, info) </td></tr><tr><td>draw3d</td><td>function</td><td>function (callback) <br><br>We need the 3D viewer to be ready to go for us to generate our 3D view,
so do a little bit of a wait sequence here where we try 3 times to
grab the 3D viewer object and then we can render our board.
Alternately, we could render our board and then inject into the 3D
viewer later. Not sure why I didn't do it that way initially.</td></tr><tr><td>colorSignal</td><td>number</td><td></td></tr><tr><td>colorSmd</td><td>number</td><td></td></tr><tr><td>colorSignalBottom</td><td>number</td><td></td></tr><tr><td>colorSmdBottom</td><td>number</td><td></td></tr><tr><td>colorVia</td><td>number</td><td></td></tr><tr><td>colorPad</td><td>number</td><td></td></tr><tr><td>colorMill</td><td>number</td><td></td></tr><tr><td>colorHole</td><td>number</td><td></td></tr><tr><td>colorsDrop</td><td>object</td><td></td></tr><tr><td>colorDimension</td><td>number</td><td></td></tr><tr><td>opacitySignal</td><td>number</td><td></td></tr><tr><td>opacityDimension</td><td>number</td><td></td></tr><tr><td>opacityVia</td><td>number</td><td></td></tr><tr><td>opacityPad</td><td>number</td><td></td></tr><tr><td>endmillSize</td><td>number</td><td></td></tr><tr><td>actualEndmill</td><td>number</td><td></td></tr><tr><td>inflateMillPathBy</td><td>object</td><td></td></tr><tr><td>paths</td><td>object</td><td></td></tr><tr><td>pathsUnion</td><td>object</td><td></td></tr><tr><td>pathsUnionHoles</td><td>object</td><td></td></tr><tr><td>threeDimensions</td><td>object</td><td></td></tr><tr><td>activeLayer</td><td>string</td><td>"Top"</td></tr><tr><td>clipperDimensions</td><td>object</td><td></td></tr><tr><td>onDraw3dReady</td><td>function</td><td>function () <br><br>This is a key method that will actually start the traversal of the
entire Eagle BRD and generate Three.js objects for each pad/smd/via/wire, etc.
Then it will generate Clipper Paths which are just 2d xy values in the
format that the Clipper library wants so we can do unions and diffs
which is important to generate the isolation paths as well as deal with
polygons that may be on the board representing signal planes like a 
GND plane.</td></tr><tr><td>onDraw3dReadyAfter</td><td>function</td><td>function () </td></tr><tr><td>clearanceHeight</td><td>number</td><td></td></tr><tr><td>depthOfSignalMilling</td><td>number</td><td></td></tr><tr><td>feedRatePlunge</td><td>number</td><td></td></tr><tr><td>feedRateSignals</td><td>number</td><td></td></tr><tr><td>feedRateDimensions</td><td>number</td><td></td></tr><tr><td>drillFeedrate</td><td>number</td><td></td></tr><tr><td>drillMaxDiameter</td><td>number</td><td></td></tr><tr><td>drillDepth</td><td>number</td><td></td></tr><tr><td>depthOfDimensions</td><td>number</td><td></td></tr><tr><td>millDiameter</td><td>number</td><td></td></tr><tr><td>stepDownDimensions</td><td>number</td><td></td></tr><tr><td>stepDownPasses</td><td>number</td><td></td></tr><tr><td>generateGcodeHole</td><td>function</td><td>function (diameter, x, y)</td></tr><tr><td>exportGcodeHeader</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeMilling</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeMarkVias</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeMarkPads</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeDrillVias</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeDrillPads</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeDimensions</td><td>function</td><td>function ()</td></tr><tr><td>exportGcodeFooter</td><td>function</td><td>function ()</td></tr><tr><td>exportGcode</td><td>function</td><td>function () </td></tr><tr><td>gcodeParts</td><td>object</td><td></td></tr><tr><td>addGcode</td><td>function</td><td>function (count, gcode)</td></tr><tr><td>getGcode</td><td>function</td><td>function () </td></tr><tr><td>setupAdvancedInflateByUI</td><td>function</td><td>function () </td></tr><tr><td>onRefresh</td><td>function</td><td>function (event, callback) </td></tr><tr><td>threePathEndMill</td><td>object</td><td></td></tr><tr><td>onRefresh2nd</td><td>function</td><td>function (event, callback) </td></tr><tr><td>getInflatePathWithConstraint</td><td>function</td><td>function (paths, inflateBy, constraints) </td></tr><tr><td>raycaster</td><td>object</td><td></td></tr><tr><td>projector</td><td>object</td><td></td></tr><tr><td>arrowHelper</td><td>object</td><td></td></tr><tr><td>intersectObjects</td><td>object</td><td></td></tr><tr><td>renderArea</td><td>object</td><td></td></tr><tr><td>infoArea</td><td>object</td><td></td></tr><tr><td>infoSignalArea</td><td>object</td><td></td></tr><tr><td>lastIntersect</td><td>object</td><td></td></tr><tr><td>hidePopupsElem</td><td>object</td><td></td></tr><tr><td>setupMouseOver</td><td>function</td><td>function () </td></tr><tr><td>reactivateMouseMove</td><td>function</td><td>function () </td></tr><tr><td>deactivateMouseMove</td><td>function</td><td>function () </td></tr><tr><td>hidePopups</td><td>function</td><td>function () </td></tr><tr><td>lastIntersectOtherMaterials</td><td>object</td><td></td></tr><tr><td>onMouseOver</td><td>function</td><td>function (event) </td></tr><tr><td>getXorOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr><td>getIntersectionOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr><td>getDiffOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr><td>getAllPathsAsOuterOrientation</td><td>function</td><td>function (subj_paths) </td></tr><tr><td>getUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr><td>drawUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr><td>drawClipperPaths</td><td>function</td><td>function (paths, color, opacity, z, zstep, isClosed, isAddDirHelper) </td></tr><tr><td>createClipperPathsAsMesh</td><td>function</td><td>function (paths, color, opacity, holePath) </td></tr><tr><td>getInflatePath</td><td>function</td><td>function (paths, delta, joinType) </td></tr><tr><td>createThermalCutoutsFromSmd</td><td>function</td><td>function (smd, poly, myInflateBy) </td></tr><tr><td>sortObjByKey</td><td>function</td><td>function (obj)</td></tr><tr><td>clipperDimension</td><td>object</td><td></td></tr><tr><td>getDimensionWires</td><td>function</td><td>function () </td></tr><tr><td>draw3dDimension</td><td>function</td><td>function (endmillSize) </td></tr><tr><td>addStrokeCapsToLine</td><td>function</td><td>function (x1, y1, x2, y2, width, capType) </td></tr><tr><td>clipperBySignalKey</td><td>object</td><td></td></tr><tr><td>clipperBySignalKeyItem</td><td>object</td><td></td></tr><tr><td>clipperSignalWires</td><td>object</td><td></td></tr><tr><td>clipperSignalPolys</td><td>object</td><td></td></tr><tr><td>draw3dVias</td><td>function</td><td>function (layersName) </td></tr><tr><td>draw3dSignalWires</td><td>function</td><td>function (layer) </td></tr><tr><td>draw3dSignalPolygons</td><td>function</td><td>function (layer) </td></tr><tr><td>clipperElements</td><td>object</td><td></td></tr><tr><td>clipperPads</td><td>object</td><td></td></tr><tr><td>clipperSmds</td><td>object</td><td></td></tr><tr><td>clipperVias</td><td>object</td><td></td></tr><tr><td>drillPads</td><td>object</td><td></td></tr><tr><td>drillVias</td><td>object</td><td></td></tr><tr><td>draw3dElements</td><td>function</td><td>function (layer) </td></tr><tr><td>rotObjectMatrix</td><td>object</td><td></td></tr><tr><td>rotateAroundObjectAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr><td>rotWorldMatrix</td><td>object</td><td></td></tr><tr><td>rotateAroundWorldAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr><td>drawCircle</td><td>function</td><td>function (x, y, radius, color)</td></tr><tr><td>drawSphere</td><td>function</td><td>function (x, y, radius, color)</td></tr><tr><td>drawSquare</td><td>function</td><td>function (x1, y1, x2, y2) </td></tr><tr><td>mySceneGroup</td><td>object</td><td></td></tr><tr><td>sceneReAddMySceneGroup</td><td>function</td><td>function () </td></tr><tr><td>sceneRemoveMySceneGroup</td><td>function</td><td>function () </td></tr><tr><td>sceneAdd</td><td>function</td><td>function (obj) </td></tr><tr><td>sceneRemove</td><td>function</td><td>function (obj) </td></tr><tr><td>draw</td><td>function</td><td>function (e) </td></tr><tr><td>onDropped</td><td>function</td><td>function (data, info) </td></tr><tr><td>onDragOver</td><td>function</td><td>function () </td></tr><tr><td>onDragLeave</td><td>function</td><td>function () </td></tr><tr><td>isVidLoaded</td><td>boolean</td><td></td></tr><tr><td>lazyLoadTutorial</td><td>function</td><td>function () </td></tr><tr><td>options</td><td>object</td><td></td></tr><tr><td>setupUiFromLocalStorage</td><td>function</td><td>function () </td></tr><tr><td>saveOptionsLocalStorage</td><td>function</td><td>function () </td></tr><tr><td>showBody</td><td>function</td><td>function (evt) </td></tr><tr><td>hideBody</td><td>function</td><td>function (evt) </td></tr><tr><td>btnSetup</td><td>function</td><td>function () </td></tr><tr><td>statusEl</td><td>object</td><td></td></tr><tr><td>status</td><td>function</td><td>function (txt) </td></tr><tr><td>forkSetup</td><td>function</td><td>function () </td></tr>
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

