# Examples

## Interactive chart features

These features will require keyboard shortcuts for keyboard-only users, as well as a way to communicate changes/updates to screen reader users.

* Tooltip
    - Individual element
    - All elements for a certain X-value
* Element interactions
    - Selecting graphical elements (typically for filtering information or other charts)
    - Dragging data points around. [Link](https://github.com/artus9033/chartjs-plugin-dragdata)
* Change orientation (Horziontal v Vertical)
* Direction (LTR, RTL)
* Multiple chart types (eg, Bar-Line)
* Hierarchical X-axis values [Link](https://github.com/sgratzl/chartjs-plugin-hierarchical)
* Zooming
* Panning
* X-axis range selector (Recharts calls it a Brush) [Link](https://recharts.org/en-US/examples/BrushBarChart)
* Subplots (plotly) / Panels (SAS)

## Visual features

These features need to be communicated to screen reader users.

* Data labels
* Regions
* Annotations

## Data features

For each chart type, we should be able to handle:

* A small number of data points (eg, 5)
* A large number of data points (eg, 5,000)
* Missing/skipped data
* Inconsistent X-values
* Date/Time formatting
* Currency formatting
* Multi-axes
    - Aesthetic (eg, Celsius and Fahrenheit)
    - Data (eg, Bar-Line plot, with bar referencing one axis, and line referencing the other)

## Legends
* Clicking legend item toggles that item [Link](https://www.chartjs.org/docs/latest/samples/bar/border-radius.html)
* Legend item orientation (row, column, matrix)
* Legend item position (top, left, right, bottom)
* Legend hover events [Link](https://www.chartjs.org/docs/latest/samples/legend/events.html)

## Chart types

Here are different chart types, as well as features or varying aesthetics used with those charts. Any keyboard-based on screen reader interactions should make sense with all of the cases.

* Bar chart
    - Single series
    - Grouped
    - Stacked
    - Grouped and Stacked
    - Area bar (eg, Marimekko)
    - Targets
    - Error bars
    - Funnels
    - Waterfall
    - Histogram
    - Radial bar chart
    - Barbell
    - Lollipop
* Line chart
    - Single series
    - Multi-series
    - Area chart
    - Line style change (eg, forecasts/projections)
    - Sparkline (no axes)
    - Spaghetti chart (lots of lines, but only some of them are highlighted)
* Scatter/Bubble plot
    - Single series
    - Multiple colors
    - Multiple shapes
    - Multiple colors and shapes
* Pie/Donut
    - Single
    - Grouped (aka "stacked", "layered", "nested")
* Polar area
* Radar
    - Single
    - Grouped (aka "stacked")
* Box plot
    - No outliers
    - 1 outlier level
    - 2+ outlier levels
    - Mean
    - Standard deviation
    - Violin plot
    - Grouped
    - Jittered data
* Candlestick
* Funnel/Pyramid
* Matrix/Heatmap
* PCP
    - Interaction: Rearrange axes [Link](https://plotly.com/javascript/parallel-coordinates-plot/)
    - Apply filters to axes
    - Highlight lines
* Treemap
* Band plot


## Out of scope

Chart types that I don't feel equipped to discuss now, but if someone else wants to take it, they can.

* Maps
* Sankey
* Arc Diagram
* Node-Link Graphs
* Smith chart
* Contour plot
* Word cloud
* Ternary plot
* Venn diagram
* 3-D anything
* Pictorals
* Treegraph/Dendrogram
* Vector graph [Link](https://www.highcharts.com/demo/highcharts/vector-plot)
* Wheel
* Flame
* Sunburst
* Waffle
* Packing
* Voronoi
* Steamgraph