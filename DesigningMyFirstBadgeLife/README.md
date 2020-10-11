# The Basics - Designing an LED Throwie

We're going to start with one of the simplest circuits for our first badge: a battery-powered LED.

1. ## Installing Kicad

   Download the latest stable version of Kicad for your operating system from the [Kicad downloads page](http://kicad-pcb.org/download/).  You should make sure it is at least v5.1.5 (that's what all the example files are saved as, if you want to compare them)

1. ## Build the schematic

   Open Kicad

   Choose `File` -> `New` -> `Project...` and give it a name

   ![Screen shot of the main KiCad window](screenshots/MainKicadScreen.png)

   Double-click on the schematic file `.sch`.  The first time you run Kicad it might ask you to "Configure Global Symbol Library Table".  Choose the recommended option.

   ![Screen shot of MainKicadScreen](screenshots/MainKicadScreen.png)

   You should now see the main blank Eeschema work area.  This is where you lay out the schematic of your circuit&mdash;the "tube map" version if you will.  It focuses on what connects to what, not on *where* each part will actually be.

   ![Screen shot of BlankEeschemaWorkArea](screenshots/BlankEeschemaWorkArea.png)

   Select `Place power port` in the Tools on the Right for from `Place/Power Port` drop down menu.  For a simple circuit like an LED throwie this is a bit of an overkill, but it's a good habit to get into for more complex circuits.

   The power ports aren't things that will show up physically in your PCB, but ways to link common connections together without having to draw wires between them all, given how common it is to want to link something to GND, for example.  (You can do a similar thing with Labels too, if you want to define your own)

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-03-44.png)

   Choose the `GND` Power flag, GND from the symbol list and then place it somewhere in the lower half of your schematic.  Don't worry too much about exactly where, you can always move it later if you need to.

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-04-20.png)

   Then repeat the process to place a `+BATT` power port, somewhere in the upper half of your schematic.  You'll end up with something like this:

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-09-28.png)

   Now we'll place the symbols that *will* translate into physical components on the finished PCB.

   Select `Place symbol` in the Tools on the Right or from `Place/Symbol` drop down menu and type `BATT` in the search window at the top.  Then choose the `Battery_Cell` symbol and place it in the work area

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-10-09.png)

   Similarly, add the `LED` symbol to the work area

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-10-43.png)

   Your work area should now look like this

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-11-25.png)

   Now add the `R_Small` symbol to the work area

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-11-48.png)

   Your work area should now look like this

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-12-23.png)

   Next we need to wire up the circuit.

   Select the green `Place wire` in the Tools on the Right or from `Place/Wire` drop down menu

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-12-34.png)

   Draw a line with the `Place wire` tool from the round end point footprint at the top of the passive resistor `R_Small` symbol to the `+BATT` symbol

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-12-48.png)

   Draw a line with the `Place wire` tool from the round end point footprint of bottom of the passive resistor `R_Small` symbol to the top of the `LED` symbol

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-12-56.png)

   Draw a wire from the round end point footprint of bottom of the `LED` symbol to the `GND` symbol

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-13-14.png)

   Draw a wire from the round end point footprint of the `-` of the `Battery_Cell` symbol to the green wire connected to the `GND` symbol. This will generate a small green dot to show that this is a junction, and means the wires are connected at that point.  Wires that cross over *without* the green dot aren't connected together, but it's best to avoid that wherever possible.

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-13-21.png)

   Draw a wire from the round end point footprint of the `+` of the `Battery_Cell` symbol to the green wire connected to the `+BATT` symbol. This will generate a junction.

   Now all of our schematic is wired up.

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-13-42.png)

   We should set the properties of the components so that anyone reading it will know what sort of components to use.

   Double click on the `Battery_Cell` to edit the value field or right click and select `Properties/Edit Value`

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-30-40.png)

   Double click on the `Battery_Cell` to edit it's Properties or right click and select `Properties/Edit Value`

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-35-15.png)

   Change the `Field Value` of the `Battery_Cell` to `CR2032`  

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-36-40.png)

   Annotate the schematic

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-41-49.png)

   Your work area should look like this

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2016-41-56.png)

1. ## Footprints and netlist

   * CR2032 holder - [CPC BT06539](https://cpc.farnell.com/pro-power/pp002088/battery-holder-coin-cell-cr2032/dp/BT06539) maps to Keystone 1060; 
   * [Digikey 36-3034CT-ND](https://www.digikey.co.uk/product-detail/en/keystone-electronics/3034TR/36-3034CT-ND/4833649) maps to Keystone 3034

   Assign Footprints in `Tools/Assign Footprints`. The first time you do this you will load up your footprints library. You may have to configure libraries for parts not included in your Kicad setup. Edit each entry in the table to match the footprints below

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2019-00-27.png)

   Generate Netlist

   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2019-00-48.png)

1. ## Lay out the PCB


   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-05-19.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-05-25.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-05-48.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-06-03.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-06-14.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-06-20.png)



   ![Screen shot of ](screenshots/Screenshot%20from%202019-05-12%2021-06-31.png)

1. ## Getting physical boards

   1. Generating Gerbers and drill file
   1. Making them...
      * Milling your own PCB
      * Sending them to a PCB fab house

