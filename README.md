# com-chilipeppr-widget-eagle
This widget lets you drag in an Eagle PCB ".brd" file to mill.

![alt text](screenshot.png "Screenshot")

## ChiliPeppr Widget / Eagle BRD v5.4

All ChiliPeppr widgets/elements are defined using cpdefine() which is a method
that mimics require.js. Each defined object must have a unique ID so it does
not conflict with other ChiliPeppr widgets.

| Item                  | Value           |
| -------------         | ------------- | 
| ID                    | com-chilipeppr-widget-eagle |
| Name                  | Widget / Eagle BRD v5.4 |
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
// Inject new div to contain widget or use an existing div with an ID
$("body").append('<' + 'div id="myDivWidgetEagle"><' + '/div>');

chilipeppr.load(
  "#myDivWidgetEagle",
  "http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html",
  function() {
    // Callback after widget loaded into #myDivWidgetEagle
    // Now use require.js to get reference to instantiated widget
    cprequire(
      ["inline:com-chilipeppr-widget-eagle"], // the id you gave your widget
      function(myObjWidgetEagle) {
        // Callback that is passed reference to the newly loaded widget
        console.log("Widget / Eagle BRD v5.4 just got loaded.", myObjWidgetEagle);
        myObjWidgetEagle.init();
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
      <tr valign="top"><td>/com-chilipeppr-widget-eagle/onAddGcode</td><td>This signal lets a 3rd party add-on inject its own Gcode into the 
            overall final Gcode for the Eagle BRD Widget. Here is an example of how to subscribe. <br><br><pre>
chilipeppr.subscribe(
    "/com-chilipeppr-widget-eagle/addGcode", 
    this, 
    this.myOnAddGcode
    );
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
            </td></tr><tr valign="top"><td>/com-chilipeppr-widget-eagle/beforeLayerGenerate</td><td>This widget fires a signal before generating the Three.js objects
                and Clipper paths for a board layer. The Three.js objects are 3D objects representing the
                pads, vias, smds, wires, polygons, and dimensions. Those Three.js objects are used to
                populate the 3D viewer and to calculate 2D Clipper paths from. <br><br>Clipper paths are the 2D XY
                values of all the layer's objects and are generated so that unions and diffs can be
                calculated on those paths in the render step. Clipper paths can be easily inflated and
                deflated by the Clipper.js library which is why they are so important to this widget.<br><br>When you get this signal a reference to "this", i.e. the Eagle Widget, is included in
                the payload so you may use it to manipulate this widget as you see fit.</td></tr><tr valign="top"><td>/com-chilipeppr-widget-eagle/afterLayerGenerate</td><td>Please see the /beforeLayerGenerate description to understand this
                signal better. The /afterLayerGenerate signal is fired after this widget is done
                generating the board layer. The payload is the same as the before signal.</td></tr><tr valign="top"><td>/com-chilipeppr-widget-eagle/beforeToolPathRender</td><td>This widget fires a signal before the rendering of the tool path 
                for the milling of the Eagle BRD. As the user tests out different inflate values, you 
                will get this signal for each re-render of the tool path the user asks for, i.e. when 
                they click the "render" button.<br><br>In the payload is a reference to "this" so you can possibly grab info or do other 
                manipulations of the board before we render the tool path. This is especially useful for add-on 
                widgets to the Eagle BRD widget such as the Solder Paste Dispenser Add-On or the
                Pick and Place Add-On.
                </td></tr><tr valign="top"><td>/com-chilipeppr-widget-eagle/afterToolPathRender</td><td>This widget fires a signal after the rendering of the tool path 
                for the Eagle BRD. The tool path is the blue line in the 3D viewer.
                Similar to the /beforeToolPathRender signal, in the payload is a reference to "this" so you can possibly grab info or do other 
                manipulations of the board after we render. This is especially useful for add-on 
                widgets to the Eagle BRD widget such as the Solder Paste Dispenser Add-On or the
                Pick and Place Add-On.
                </td></tr>    
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
      <tr valign="top"><td>/com-chilipeppr-widget-eagle/getBoardData</td><td>Call this with a callback and you will immediately get back the baord data
                to your callback. Call like 
                chilipeppr.publish("/com-chilipeppr-eagle/getBoardData", mycallback);
                This returns all of the board data for you, so that you can know
                all of the information that this Eagle BRD widget created. You will get back data like:
                {
                    clipperBySignalKey: {}, // contains all signals (wires)
                    clipperDimension: {}, // contains dimension of board
                    clipperElements: {},
                    clipperPads: {}, // contains all pads (pads have holes)
                    clipperSignalPolys: {}, // polygons that are signals like a GND plane
                    clipperSignalWires: {}, // wires by name
                    clipperSmds: {}, // all the smd pads, i.e. where components sit for soldering
                    clipperVias: {}, // your vias. these have holes too.
                    eagle: {}, // the parsed Eagle BRD XML into a structure
                }</td></tr>    
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
      <tr valign="top"><td>/com-chilipeppr-widget-eagle/com-chilipeppr-elem-dragdrop/ondropped</td><td>We subscribe to this signal at a higher priority to intercept the signal, double check if it is an Eagle Brd file and if so, we do not let it propagate by returning false. That way the 3D Viewer, Gcode widget, or other widgets will not get Eagle Brd file drag/drop events because they will not know how to interpret them.</td></tr>    
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
      <tr valign="top"><td>id</td><td>string</td><td>"com-chilipeppr-widget-eagle"<br><br>The ID of the widget. You must define this and make it unique.</td></tr><tr valign="top"><td>name</td><td>string</td><td>"Widget / Eagle BRD v5.4"</td></tr><tr valign="top"><td>desc</td><td>string</td><td>"This widget lets you drag in an Eagle PCB \".brd\" file to mill."</td></tr><tr valign="top"><td>url</td><td>string</td><td>"http://raw.githubusercontent.com/chilipeppr/widget-eagle/master/auto-generated-widget.html"</td></tr><tr valign="top"><td>fiddleurl</td><td>string</td><td>"http://ide.c9.io/chilipeppr/widget-eagle"</td></tr><tr valign="top"><td>githuburl</td><td>string</td><td>"http://github.com/chilipeppr/widget-eagle"</td></tr><tr valign="top"><td>testurl</td><td>string</td><td>"http://widget-eagle-chilipeppr.c9users.io/widget.html"</td></tr><tr valign="top"><td>publish</td><td>object</td><td>Please see docs above.<br><br>Define the publish signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>subscribe</td><td>object</td><td>Please see docs above.<br><br>Define the subscribe signals that this widget/element owns or defines so that
other widgets know how to subscribe to them and what they do.</td></tr><tr valign="top"><td>foreignPublish</td><td>object</td><td>Please see docs above.<br><br>Document the foreign publish signals, i.e. signals owned by other widgets
or elements, that this widget/element publishes to.</td></tr><tr valign="top"><td>foreignSubscribe</td><td>object</td><td>Please see docs above.<br><br>Document the foreign subscribe signals, i.e. signals owned by other widgets
or elements, that this widget/element subscribes to.</td></tr><tr valign="top"><td>init</td><td>function</td><td>function (doMyOwnDragDrop) <br><br>All widgets should have an init method. It should be run by the
instantiating code like a workspace or a different widget.<br><br>If you are doing development on this widget, it's important to understand what
data is available to you after the board is parsed. This data can enable you to
do enhanced operations. For example, I'm working on creating laser paths to laser
out the solder mask to reveal the underlying pads and smds. I had to re-figure out
what data is available to figure out those laser paths. Here's my summary. -Jlauer<br><br>Why clipper? Clipper is the library used to do boolean operations on polygons. Eagle
gives us XY values for everything, and if we are to combine those into overall paths
for milling, etc, then we need to merge those polygons. The clipper items below represent
the clean final version of all that merging.<br><br>clipperBySignalKey: {}, // contains all signals (wires)
clipperDimension: {}, // contains dimension of board
clipperElements: {},
clipperPads: {}, // contains all pads (pads have holes)
clipperSignalPolys: {}, // polygons that are signals like a GND plane
clipperSignalWires: {}, // wires by name
clipperSmds: {}, // all the smd pads, i.e. where components sit for soldering
clipperVias: {}, // your vias. these have holes too.
eagle: {}, // the parsed Eagle BRD XML into a structure</td></tr><tr valign="top"><td>blankBoard</td><td>object</td><td></td></tr><tr valign="top"><td>blankBoardSceneGroup</td><td>object</td><td></td></tr><tr valign="top"><td>setupBlankBoardParamenters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeBlankBoardParamenters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>draw3dBlankBoard</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>regHoles</td><td>object</td><td></td></tr><tr valign="top"><td>regHoleGcodePara</td><td>object</td><td></td></tr><tr valign="top"><td>regHolesSceneGroup</td><td>object</td><td></td></tr><tr valign="top"><td>setupRegHolesParamenters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeRegHolesGcodeParamenters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeRegHolesParamenters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>getRegHoles</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>draw3dRegHoles</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeRegistrationHoles</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sendRegHoleGcodeToWorkspace</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>setupSolderMaskTab</td><td>function</td><td>function () <br><br>This sets up the tab to generate solder mask Gcode.</td></tr><tr valign="top"><td>solderMaskRenderHide</td><td>function</td><td>function () </td></tr><tr valign="top"><td>solderMaskGrp</td><td>object</td><td></td></tr><tr valign="top"><td>solderMaskGcodePath</td><td>object</td><td></td></tr><tr valign="top"><td>solderMaskRender</td><td>function</td><td>function () <br><br>Look at all the pads/smds and render a path based on what the user gave us in
the solder mask tab.</td></tr><tr valign="top"><td>solderMaskRenderCallback</td><td>function</td><td>function () </td></tr><tr valign="top"><td>solderMaskRenderInvert</td><td>function</td><td>function (opts) <br><br>This method renders an inverse path for lasering/milling. This can be used
to expose a solder mask with UV laser light outside of the pads. Then the
pads can be washed off to expose the copper.<br><br>opts = {
width: w,
isShowAsMesh: isShowAsMesh,
isOutlineOnly: isOutlineOnly,
outlineOut: outlineOut,
outlineOn: outlineOn,
outlineIn: outlineIn,
gcodePath: this.solderMaskGcodePath,
// threeGrp: this.solderMaskGrp,
padsAndSmds: padsAndSmds,
clipperDimension: this.clipperDimension,
}</td></tr><tr valign="top"><td>solderMaskRenderInvertCallback</td><td>function</td><td>function (opts) </td></tr><tr valign="top"><td>solderMaskGenerateGcodeTimeoutPtr</td><td>object</td><td></td></tr><tr valign="top"><td>solderMaskIsGcodeInRegeneratingState</td><td>boolean</td><td></td></tr><tr valign="top"><td>solderMaskGenerateGcode</td><td>function</td><td>function () <br><br>This method will trigger a process to generateGcode however, it
allows this to be called a bunch of times and it will always wait
to do the generate about 1 second later and de-dupe the multiple calls.</td></tr><tr valign="top"><td>solderMaskGenerateGcodeCallback</td><td>function</td><td>function () <br><br>Iterate over the text3d that was generated and create
Gcode to mill/cut the three.js object.</td></tr><tr valign="top"><td>solderMaskSendGcodeToWorkspace</td><td>function</td><td>function () </td></tr><tr valign="top"><td>drawPathAsLineOrMesh</td><td>function</td><td>function (clipperPath, width, isShowAsMesh, threeGroup) <br><br>Pass in a clipper path and we will draw the line or inflate the line to a nice looking mesh.
This is used to draw end mill paths that are the width of the line.</td></tr><tr valign="top"><td>getCentroid</td><td>function</td><td>function ( mesh ) </td></tr><tr valign="top"><td>mirrorX</td><td>boolean</td><td></td></tr><tr valign="top"><td>mirrorY</td><td>boolean</td><td></td></tr><tr valign="top"><td>setupMirrorAxis</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeMirrorAxis</td><td>function</td><td>function () </td></tr><tr valign="top"><td>tabs</td><td>object</td><td></td></tr><tr valign="top"><td>setupTabParameters</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeTabWidth</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>onChangeTabHeight</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>onChangeTabParameter</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>setupLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr valign="top"><td>populateLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onChangeLayerToggleDropdown</td><td>function</td><td>function () </td></tr><tr valign="top"><td>ThreeAxisX</td><td>object</td><td></td></tr><tr valign="top"><td>ThreeAxisY</td><td>object</td><td></td></tr><tr valign="top"><td>ThreeAxisZ</td><td>object</td><td></td></tr><tr valign="top"><td>deg180toRad</td><td>object</td><td></td></tr><tr valign="top"><td>setupFrequentThreeFeatures</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupFeedsDepths</td><td>function</td><td>function () </td></tr><tr valign="top"><td>calcPasses</td><td>function</td><td>function (el) </td></tr><tr valign="top"><td>activateWidget</td><td>function</td><td>function () <br><br>This method is called from the main workspace telling us the user
just activated us as a widget. This is not the same as load. Load
happens once. Activate happens many times if user closes then opens
us.</td></tr><tr valign="top"><td>unactivateWidget</td><td>function</td><td>function () </td></tr><tr valign="top"><td>init3d</td><td>function</td><td>function () <br><br>Try to get a reference to the 3D viewer.</td></tr><tr valign="top"><td>onInit3dSuccess</td><td>function</td><td>function () </td></tr><tr valign="top"><td>obj3d</td><td>object</td><td></td></tr><tr valign="top"><td>obj3dmeta</td><td>object</td><td></td></tr><tr valign="top"><td>userCallbackForGet3dObj</td><td>object</td><td></td></tr><tr valign="top"><td>get3dObj</td><td>function</td><td>function (callback) </td></tr><tr valign="top"><td>get3dObjCallback</td><td>function</td><td>function (data, meta) </td></tr><tr valign="top"><td>is3dViewerReady</td><td>boolean</td><td></td></tr><tr valign="top"><td>clear3dViewer</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearEagleBrd</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearEagleBrdStep2</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupGcodeTab</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sendGcodeToWorkspace</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupDragDrop</td><td>function</td><td>function () </td></tr><tr valign="top"><td>eagle</td><td>object</td><td></td></tr><tr valign="top"><td>open</td><td>function</td><td>function (data, info) </td></tr><tr valign="top"><td>draw3d</td><td>function</td><td>function (callback) <br><br>We need the 3D viewer to be ready to go for us to generate our 3D view,
so do a little bit of a wait sequence here where we try 3 times to
grab the 3D viewer object and then we can render our board.
Alternately, we could render our board and then inject into the 3D
viewer later. Not sure why I didn't do it that way initially.</td></tr><tr valign="top"><td>colorSignal</td><td>number</td><td></td></tr><tr valign="top"><td>colorSmd</td><td>number</td><td></td></tr><tr valign="top"><td>colorSignalBottom</td><td>number</td><td></td></tr><tr valign="top"><td>colorSmdBottom</td><td>number</td><td></td></tr><tr valign="top"><td>colorVia</td><td>number</td><td></td></tr><tr valign="top"><td>colorPad</td><td>number</td><td></td></tr><tr valign="top"><td>colorMill</td><td>number</td><td></td></tr><tr valign="top"><td>colorHole</td><td>number</td><td></td></tr><tr valign="top"><td>colorHoleUnhandled</td><td>number</td><td></td></tr><tr valign="top"><td>colorsDrop</td><td>object</td><td></td></tr><tr valign="top"><td>colorDimension</td><td>number</td><td></td></tr><tr valign="top"><td>colorTabs</td><td>number</td><td></td></tr><tr valign="top"><td>colorMilling</td><td>number</td><td></td></tr><tr valign="top"><td>colorFailed</td><td>number</td><td></td></tr><tr valign="top"><td>opacitySignal</td><td>number</td><td></td></tr><tr valign="top"><td>opacityDimension</td><td>number</td><td></td></tr><tr valign="top"><td>opacityTabs</td><td>number</td><td></td></tr><tr valign="top"><td>opacityVia</td><td>number</td><td></td></tr><tr valign="top"><td>opacityPad</td><td>number</td><td></td></tr><tr valign="top"><td>endmillSize</td><td>number</td><td></td></tr><tr valign="top"><td>actualEndmill</td><td>number</td><td></td></tr><tr valign="top"><td>inflateMillPathBy</td><td>object</td><td></td></tr><tr valign="top"><td>paths</td><td>object</td><td></td></tr><tr valign="top"><td>pathsUnion</td><td>object</td><td></td></tr><tr valign="top"><td>pathsUnionHoles</td><td>object</td><td></td></tr><tr valign="top"><td>boardBoundaries</td><td>object</td><td></td></tr><tr valign="top"><td>blankBoundaries</td><td>object</td><td></td></tr><tr valign="top"><td>activeLayer</td><td>string</td><td>"Top"</td></tr><tr valign="top"><td>clipperDimensions</td><td>object</td><td></td></tr><tr valign="top"><td>onDraw3dReady</td><td>function</td><td>function () <br><br>This is a key method that will actually start the traversal of the
entire Eagle BRD and generate Three.js objects for each pad/smd/via/wire, etc.
Then it will generate Clipper Paths which are just 2d xy values in the
format that the Clipper library wants so we can do unions and diffs
which is important to generate the isolation paths as well as deal with
polygons that may be on the board representing signal planes like a 
GND plane.</td></tr><tr valign="top"><td>onDraw3dReadyAfter</td><td>function</td><td>function () </td></tr><tr valign="top"><td>clearanceHeight</td><td>number</td><td></td></tr><tr valign="top"><td>depthOfSignalMilling</td><td>number</td><td></td></tr><tr valign="top"><td>feedRatePlunge</td><td>number</td><td></td></tr><tr valign="top"><td>feedRateSignals</td><td>number</td><td></td></tr><tr valign="top"><td>feedRateDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>drillFeedrate</td><td>number</td><td></td></tr><tr valign="top"><td>drillMaxDiameter</td><td>number</td><td></td></tr><tr valign="top"><td>drillDepth</td><td>number</td><td></td></tr><tr valign="top"><td>depthOfDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>millDiameter</td><td>number</td><td></td></tr><tr valign="top"><td>millDiameterMin</td><td>number</td><td></td></tr><tr valign="top"><td>useDimensionLayer</td><td>boolean</td><td></td></tr><tr valign="top"><td>useMillingLayer</td><td>boolean</td><td></td></tr><tr valign="top"><td>cuttingToolOption</td><td>number</td><td></td></tr><tr valign="top"><td>minWireWidthToMill</td><td>number</td><td></td></tr><tr valign="top"><td>ignoreSmallWires</td><td>boolean</td><td></td></tr><tr valign="top"><td>stepDownDimensions</td><td>number</td><td></td></tr><tr valign="top"><td>stepDownPasses</td><td>number</td><td></td></tr><tr valign="top"><td>spindleRPM</td><td>number</td><td></td></tr><tr valign="top"><td>exportGcodeHeader</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMilling</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMarkHoles</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeDrillHoles</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcodeMillHoles</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>getBoardDimensionsToMill</td><td>function</td><td>function ()<br><br>This function will create inflate/deflate board dimension paths without using ClipperLib 
the resulting path(s) will be an array of lines and curves, this was necessary to implement the Tabs feature
introduced in V5.4, as a redults curves will be rendered as G02/G03 gcode command.</td></tr><tr valign="top"><td>fixAngle</td><td>function</td><td>function (angle)</td></tr><tr valign="top"><td>exportGcodeDimensions</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>getDimensionGcode</td><td>function</td><td>function (v2, v1, z, isOpen, curve)</td></tr><tr valign="top"><td>round</td><td>function</td><td>function (n)</td></tr><tr valign="top"><td>exportGcodeFooter</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>exportGcode</td><td>function</td><td>function () </td></tr><tr valign="top"><td>gcodeParts</td><td>object</td><td></td></tr><tr valign="top"><td>addGcode</td><td>function</td><td>function (count, gcode)</td></tr><tr valign="top"><td>getGcode</td><td>function</td><td>function () </td></tr><tr valign="top"><td>setupAdvancedInflateByUI</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onFullRefresh</td><td>function</td><td>function (event, callback) </td></tr><tr valign="top"><td>onRefresh</td><td>function</td><td>function (event, callback) </td></tr><tr valign="top"><td>threePathEndMill</td><td>object</td><td></td></tr><tr valign="top"><td>onRefresh2nd</td><td>function</td><td>function (event, callback) </td></tr><tr valign="top"><td>getInflatePathWithConstraint</td><td>function</td><td>function (paths, inflateBy, constraints) </td></tr><tr valign="top"><td>raycaster</td><td>object</td><td></td></tr><tr valign="top"><td>projector</td><td>object</td><td></td></tr><tr valign="top"><td>arrowHelper</td><td>object</td><td></td></tr><tr valign="top"><td>intersectObjects</td><td>object</td><td></td></tr><tr valign="top"><td>renderArea</td><td>object</td><td></td></tr><tr valign="top"><td>infoArea</td><td>object</td><td></td></tr><tr valign="top"><td>infoSignalArea</td><td>object</td><td></td></tr><tr valign="top"><td>lastIntersect</td><td>object</td><td></td></tr><tr valign="top"><td>hidePopupsElem</td><td>object</td><td></td></tr><tr valign="top"><td>setupMouseOver</td><td>function</td><td>function () </td></tr><tr valign="top"><td>reactivateMouseMove</td><td>function</td><td>function () </td></tr><tr valign="top"><td>deactivateMouseMove</td><td>function</td><td>function () </td></tr><tr valign="top"><td>hidePopups</td><td>function</td><td>function () </td></tr><tr valign="top"><td>lastIntersectOtherMaterials</td><td>object</td><td></td></tr><tr valign="top"><td>onMouseOver</td><td>function</td><td>function (event) </td></tr><tr valign="top"><td>getXorOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getIntersectionOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getDiffOfClipperPaths</td><td>function</td><td>function (subj_paths, clip_paths) </td></tr><tr valign="top"><td>getAllPathsAsOuterOrientation</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>getUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>drawUnionOfClipperPaths</td><td>function</td><td>function (subj_paths) </td></tr><tr valign="top"><td>drawClipperPaths</td><td>function</td><td>function (paths, color, opacity, z, zstep, isClosed, isAddDirHelper) </td></tr><tr valign="top"><td>createClipperPathsAsMesh_XXX</td><td>function</td><td>function (paths, color, opacity, holePath) </td></tr><tr valign="top"><td>createClipperPathsAsMesh</td><td>function</td><td>function (paths, color, opacity, holePath, depth)</td></tr><tr valign="top"><td>getMeshLineFromClipperPath</td><td>function</td><td>function (opts) <br><br>This method is used to show the milling/laser path of a line by creating a cyan
mesh of the width of the line. You pass in the line as a Clipper Path. That means
we treat the Clipper polygon as if it's the trace line.
opts = {
width: 1, // width of line
clipperPath: [[]], // typical array of array
isSolid: true,  // if false then just shows outline
color: 0x0000ff, // blue default
opacity: 0.3, // 0 transparent to 1 non-transparent
}
Returns: THREE.Group of meshes</td></tr><tr valign="top"><td>getInflatePath</td><td>function</td><td>function (paths, delta, joinType) <br><br>Enormously useful function to inflate or deflate clipper paths. Pass
in the array of array like all normal clipper dimensions are. Then pass
in a pos/neg number for how much to inflate or deflate by. So to inflate by
0.5mm then pass in 0.5. To deflate 0.8mm pass in -0.8. For joinType the
default is ClipperLib.JoinType.jtRound. See ClipperLib docs for joinType or
leave empty.</td></tr><tr valign="top"><td>getInflateOpenPath</td><td>function</td><td>function (paths, delta, joinType) </td></tr><tr valign="top"><td>createThermalCutoutsFromSmd</td><td>function</td><td>function (smd, poly, myInflateBy) </td></tr><tr valign="top"><td>sortObjByKey</td><td>function</td><td>function (obj)</td></tr><tr valign="top"><td>wiresConnected</td><td>function</td><td>function (w1, w2)</td></tr><tr valign="top"><td>wiresConnectedF</td><td>function</td><td>function (w1, w2)</td></tr><tr valign="top"><td>wiresConnectedB</td><td>function</td><td>function (w1, w2)</td></tr><tr valign="top"><td>clipperDimension</td><td>object</td><td></td></tr><tr valign="top"><td>buildDimensionClipper</td><td>function</td><td>function () </td></tr><tr valign="top"><td>draw3dDimension</td><td>function</td><td>function () </td></tr><tr valign="top"><td>draw3dTabs</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>getTabMesh</td><td>function</td><td>function (width, d)</td></tr><tr valign="top"><td>addStrokeCapsToLine</td><td>function</td><td>function (x1, y1, x2, y2, width, capType) </td></tr><tr valign="top"><td>clipperBySignalKey</td><td>object</td><td></td></tr><tr valign="top"><td>clipperBySignalKeyItem</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSignalWires</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSignalPolys</td><td>object</td><td></td></tr><tr valign="top"><td>draw3dHoles</td><td>function</td><td>function ()//V5.2D20170105 Added</td></tr><tr valign="top"><td>draw3dVias</td><td>function</td><td>function (layersName) </td></tr><tr valign="top"><td>draw3dSignalWires</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>draw3dSignalPolygons</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>clipperElements</td><td>object</td><td></td></tr><tr valign="top"><td>clipperPads</td><td>object</td><td></td></tr><tr valign="top"><td>clipperSmds</td><td>object</td><td></td></tr><tr valign="top"><td>clipperVias</td><td>object</td><td></td></tr><tr valign="top"><td>holesToDrill</td><td>object</td><td></td></tr><tr valign="top"><td>holesToMill</td><td>object</td><td></td></tr><tr valign="top"><td>holesUnhandledCount</td><td>number</td><td></td></tr><tr valign="top"><td>addHole</td><td>function</td><td>function (drill, x, y)//V5.2D20170105 Added</td></tr><tr valign="top"><td>draw3dElements</td><td>function</td><td>function (layer) </td></tr><tr valign="top"><td>rotObjectMatrix</td><td>object</td><td></td></tr><tr valign="top"><td>rotateAroundObjectAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr valign="top"><td>rotWorldMatrix</td><td>object</td><td></td></tr><tr valign="top"><td>rotateAroundWorldAxis</td><td>function</td><td>function (object, axis, radians) </td></tr><tr valign="top"><td>boundries</td><td>function</td><td>function ()</td></tr><tr valign="top"><td>flipX</td><td>function</td><td>function (x)<br><br>Recalculate value of X if board is being mirrored</td></tr><tr valign="top"><td>flipY</td><td>function</td><td>function (y)<br><br>Recalculate value of Y if board is being mirrored</td></tr><tr valign="top"><td>flipObject3D</td><td>function</td><td>function (o)<br><br>Mirror Object3D (smdgroups and padgroups) if board is being mirrored
this function must be called before setting the position of the group</td></tr><tr valign="top"><td>drawCircle</td><td>function</td><td>function (x, y, radius, color, seg, opacity)</td></tr><tr valign="top"><td>drawSquare2</td><td>function</td><td>function (x, y, w, color)</td></tr><tr valign="top"><td>getCurveParameters</td><td>function</td><td>function (x1, y1, x2, y2, curve)</td></tr><tr valign="top"><td>drawArc</td><td>function</td><td>function (x1, y1, x2, y2, curve, color)</td></tr><tr valign="top"><td>drawSphere</td><td>function</td><td>function (x, y, radius, color)</td></tr><tr valign="top"><td>drawSquare</td><td>function</td><td>function (x1, y1, x2, y2) </td></tr><tr valign="top"><td>mySceneGroup</td><td>object</td><td></td></tr><tr valign="top"><td>sceneReAddMySceneGroup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sceneRemoveMySceneGroup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>sceneAdd</td><td>function</td><td>function (obj) </td></tr><tr valign="top"><td>sceneRemove</td><td>function</td><td>function (obj) </td></tr><tr valign="top"><td>draw</td><td>function</td><td>function (e) </td></tr><tr valign="top"><td>onDropped</td><td>function</td><td>function (data, info) </td></tr><tr valign="top"><td>onDragOver</td><td>function</td><td>function () </td></tr><tr valign="top"><td>onDragLeave</td><td>function</td><td>function () </td></tr><tr valign="top"><td>isVidLoaded</td><td>boolean</td><td></td></tr><tr valign="top"><td>lazyLoadTutorial</td><td>function</td><td>function () </td></tr><tr valign="top"><td>options</td><td>object</td><td></td></tr><tr valign="top"><td>setupUiFromLocalStorage</td><td>function</td><td>function () </td></tr><tr valign="top"><td>saveOptionsLocalStorage</td><td>function</td><td>function () </td></tr><tr valign="top"><td>showBody</td><td>function</td><td>function (evt) </td></tr><tr valign="top"><td>hideBody</td><td>function</td><td>function (evt) </td></tr><tr valign="top"><td>btnSetup</td><td>function</td><td>function () </td></tr><tr valign="top"><td>statusEl</td><td>object</td><td></td></tr><tr valign="top"><td>status</td><td>function</td><td>function (txt) </td></tr><tr valign="top"><td>forkSetup</td><td>function</td><td>function () </td></tr>
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

