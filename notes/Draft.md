# Interactions

The most common form of mouse-based user interactions are:
* Tooltips. Using a mouse to hover over individual graph elements, causing visual changes (color change, border change, size change, halo effects, etc) and/or a tooltip (box with data related to the graph element) to appear near the graph element.
* Zooming
* Panning
* Selecting 1+ graph elements.
* Activating elements
* Crosshairs

Let’s look at how to make each item accessible.

:::note
If the interaction does not exist for a mouse user, it is not necessary to add the interaction just for the keyboard-only or screen reader user. We are not saying that every interaction must be implemented to be accessible.
However, if you implement an interaction for a mouse user, you must provide an accessible version of that interaction for keyboard-only and screen reader users.
:::

## Tooltips
Typically, a mouse user will hover over individual graph elements. The graph elements may show a “hover effect” (changing color, changing border, changing size, or other effects). A tooltip, a box with data related to the graph element, will appear near the graph element. A mouse user can navigate between different graph elements by moving the mouse around the screen. As the user navigates from one element to another the tooltip will disappear and reappear with updated data, based on which element loses/gains the hover effect.
For a keyboard-only user, you need to be able to get focus on the chart, and then use the left/right arrow keys to move left/right across a chart. You should also be able to use Home to move to the origin (left for a left-to-right chart, right for a right-to-left chart), and End to move to the opposite side. The visual hover effects that mouse user see should be applied to the graph elements in “focus”.
For a screen reader-only user, the keyboard-only interactions are sufficient for navigation. However, the information provided in the tooltip will ne

## Zooming
Typically, a mouse user can zoom in/out of a using a variety of options. Sometimes, there are +/- buttons on a page. Sometimes, a mouse user can move their mouse to a point on the chart and use the mouse wheel to zoom in and out on that point.
For a keyboard-only user, the keyboard shortcut `Ctrl`+`+` and `Ctrl`+`-` should zoom the chart in and out. 

:::question
Should the focus point be based on the center of the graph, or based on the in-focus graph element?
:::

For a screen reader user, after zooming in/out, there should be feedback that, at minimum, indicates that zooming happened. Users should be able to track their own zoom level AND if the number of data points has change. This can be done by specifying the delta ("Zoomed in by 10%", "Added 15 data points") or the current state ("125% Zoom", "Showing 12 data points"). Users may differ on their preference for how the information is conveyed, and it may be up to you to balance information level versus chattiness. Below are examples of ways to communicate the information, and there will not be a consensus on which one is best
* The least you can do: Zoom out
* Current state: Zoom out. 125%. 12 data points
* Delta: Zoom out by 25%. Added 3 data points

## Panning
Typically, a mouse user can pan around the chart by clicking a mouse button and dragging the chart. Sometimes, people could also use the left/right/up/down arrow keys to pan the chart. (Since the arrow keys need to be used by keyboard-only users to navigate individual data point, do not use naked arrow keys to pan a chart).

:::question
What keyboard interactions are typically used for panning? See slippy maps (Google Maps, OpenStreetMap), whiteboarding tools (Miro, Vizio), etc
:::

## Tab stops
* Legends
* Graphical elements - all should be a single tab stop, and you should navigate between elements using left/right arrow keys and home/end
* Controls, filters, toolbars, menu buttons, etc. These should follow usual ARIA best practices.

Tab stops should be in a logical order, generally following left-right/top-down. If the legend is above the graphical elements, it should be first in the tab order.

### Legends

#### Focus
- The first legend item should receive focus (Top-Left in LTR languages, Top-Right in RTL languages).
- When legend item receives focus, a screen reader should have access to the content of the item.
Legend items should have a visible focus indicator when they are in focus
- Optionally, if there are purely aesthetic hover effects (adding a halo, adding a drop shadow, making the text bold, etc), you can replicate the effect when the element is in focus.
- If there is an informational hover effect (the related data is highlighted, the legend item gets a tooltip, or something else on the page changes in some way), that hover effect MUST be replicated when the legend item is in focus.
- If focusing on a legend item causes a change somewhere else on the page, a screen reader user must be told about that change. That update must provide the minimum necessary for the user to investigate the change further. “Page updated” is insufficient. “Info Box A updated” is sufficient.
- If a user navigates away from the legend and returns, the item that was last in focus SHOULD be in focus again.


#### Movement
- Left/right arrow keys should navigate between legend items. This applies when the legend items are list left-to-right, or top-to-bottom. Left should move left/up, and right should move right/down.
- Home/end should navigate between the first/last legend item. In a horizontal list in an ltr language, Home would go to the top left, and End would go to the bottom right. In an rtl language, Home would go to the top right, and End would go to the bottom left.
- **Optionally**, you can use the up/down arrow keys to navigate up/down, if applicable to your legend.

#### Actions
- If you can mouse click on a legend item to perform an action, a keyboard-only user should be able to press ENTER or SPACEBAR to perform the same action.
- If the legend item is togglable, the togglability and toggle state MUST be communicated to the screen reader user.
- If actions performed on legend items causes a change somewhere else on the page, screen reader users should be meaningfully informed.

### Graphical element: Navigation

#### Focus
- There should be a clear focus indicator around the graphical element in focus.
- If a tooltip appears when a mouse user hovers over a graphical element, the tooltip should appear when that element has focus.
- A screen reader user should have access to the content of the tooltip. This can be done by making the tooltip a live region, or by marking up the element to have a label that is equivalent to the tooltip.

#### Navigation
- Left/right arrow keys should navigate between graphical elements.
- Home/end should go to the first and last element.
- Sometimes, data comes in multiple series. Sometimes, tooltips appear for all series at once - in which case, you can ignore the rest of this bullet point. If you have a chart with multiple series, and each series is focusable individually, you will need to provide a way to move between series. Use Page Up and Page Down to navigate between series. However, there are basically 2 ways to determine which point to move to on the new series. Both have Pros and Cons, depending on the layout of data. While the first one is more likely to be the best, both are acceptable.
    - When moving from series A to series B, choose the element on series B that has the closest X-axis value to the item focused on series A. Pros: It’s intuitive. Cons: Computationally difficult. Could involve inconsistent movement 
    - When moving from series A to series B, choose the element on series B that has the same index as the item from series A. Pros: computationally easy. Cons: Potentially causes focus to jump around on the screen.
- Sometimes, some chart types have sub-data. For example, a bar chart could have error bars. The graphical element of the bar contains the bar’s actual value, as well as its upper/lower error bar values. If the tooltip captures all of this information simultaneously, the entire bar/errors can be considered a single element. However, if the sub-data is independently focus-able, you should navigate between sub-data using the up/down arrow keys.
- Orientation of the chart doesn't matter. If the chart is vertical, you should still use left/right arrow keys to navigate between bars. While this may not be intuitive for sighted, keyboard-only users, it provides consistency for screen reader users, and is quickly discoverable by keyboard-only users.

#### Actions
- To activate an element (eg, where a mouse user would click), use enter. A screen reader user should be informed that the element can be activated. (eg, Monday, $10, clickable)
- To select or de-select an element (eg, where a mouse user would drag a selection box), use spacebar. A screen reader user should be informed that the element is selectable, as well as the selection state, and when that selection state changes.
- To open a context menu on an element (eg, where a mouse user would right click), use Shift+F10.