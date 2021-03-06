Capacity Planning Chart
=======================
By [Jay Thoden val Velzen](http://scn.sap.com/people/jay.thodenvanvelzen)

In this chart, we show a total of 12 data elements (all measures) mapped against a Date range (the X-axis) of months. This was a chart type that came to us from a customer who asked "can you do this?". And yes, we can...

The chart is used for capacity planning. There are 3 main sections within the chart:

1. Grey shaded areas that show Base Capacity (In House), Max. Capacity (In House) and Max. Capacity (incl. subcontracting)
2. blue/ligh-blue (past) and green/red/yellow (present) bars represent Direct Labor Completed Hours, Subcontracting previous month; and Orders on Hand: Released, Orders on Hand: Not Released, and Sales Forecast
3. 3 lines (black, different dashes/solid): Full Absorption Line, Backlog, Backlog Previous Year

The chart looks at the dataset and determines where "current" is (i.e. in between where data for the past stops, and data for the future begins) and plots the various data elements accordingly. 

Because of the complexity of the chart, the importance of placement of specific data elements and the semantic use of color, all data elements are hard-coded, as are the colors. For a chart where the data is this close to the visualization and the chart itself is likely quite unique, that's perfectly fine.

D3.js/SVG tricks
----------------
The actual D3.js code is not particularly special in that is uses obscure features or anything. The complexity largely comes from having to think what to paint first and what next, considering the data elements will overlap, and z-order (and order of "painting") is therefore important. 

The order of painting therefore is in the order of the list above. You want the shaded grey areas painted first, as everything else is on top of it. We then draw the bars (past and present) and finally the lines, as these sit on top. Finally, we end with a legend.

Data file
---------
The main trick in the data file is that we have a large number of missing values (there is a clear cut-off at "present") and handle that appropriately. To test, use the .profile file in VizPacker to create the extension, and drop the bundle folder into $LUMIRA_HOME/Desktop/extensions/bundles. Open Lumira and upload the data file, then pick the extension. Drop Month into Dimensions/Data, all other data elements in Measures.

Files
------
* `Capacity Planning.lums` - Sample Lumira file
* `capacity_planning.csv` - Sample dataset
* `sap.viz.ext.capacityplanning.zip` - Extension file

Data Binding
------------
<strong>Measures</strong>
* Backlog
* Base Capacity (In House)
* Completed Hours
* Direct Labor Completed Hours
* Full Absorption Line
* Maximum Capacity (In House)
* Maximum Capacity (incl. subcontracting)
* Orders on Hand: Not Released
* Orders on Hand: Released
* Sales Forecast* 

<strong>Dimensions</strong>
* Month

Resources
---------
* Blog [Two unusual Lumira extensions: Extended Bars and Capacity Planning](http://scn.sap.com/community/lumira/blog/2015/02/03/two-unusual-lumira-extensions-extended-bars-and-capacity-planning)
