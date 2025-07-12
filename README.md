# Interactive Munin Layout

This project provides a modern, interactive single-page layout for viewing Munin-generated graphs. It transforms the default static HTML table into a responsive, filterable, and multi-metric analysis tool, making it significantly easier to navigate and correlate data from a large number of hosts.

It's a single, self-contained `index.html` file that can be dropped into any web server or opened locally.

## Features

*   **Immersive, Graphs-First View:** The page loads with a clean, uncluttered grid of graphs. All controls are hidden until you need them.
*   **Instant "Type-to-Filter" Search:** Simply start typing any character to bring up the filter bar. The grid updates instantly as you type, supporting both plain text and regular expressions.
*   **Multi-Metric and Multi-Period Views:**
    *   **Graph Type Selector:** Instantly switch between different metrics like **Traffic** (`if_bytes`) and **Uptime**.
    *   **Time Period Selector:** Easily toggle all graphs between `Day`, `Week`, `Month`, and `Year` views.
*   **Advanced Overlay Comparison Mode:**
    *   **Blended View:** Toggling "Overlay" mode stacks all currently filtered graphs, using CSS `mix-blend-mode` to make their white backgrounds transparent. This creates a powerful composite view for spotting outliers and correlations.
    *   **Isolate on Hover:** Below the blended graph, a list of all active switches appears. Hovering your mouse over any switch name in the list instantly isolates its graph, making it fully opaque and clear for inspection.
*   **Dynamic Zoom and Reflow:**
    *   An intuitive slider in the header lets you zoom the graph cards in and out.
    *   The grid automatically reflows, calculating the optimal number of columns to fit any screen size or zoom level.
*   **Zero Dependencies & Easy Setup:**
    *   The entire application is a **single, self-contained `index.html` file**.
    *   Written in vanilla HTML, CSS, and JavaScript. No build process, dependencies, or server-side code is required.

## How It Works

The core of the project is a JavaScript array containing the names of the monitored hosts. It leverages Munin's predictable URL structure to dynamically generate the correct image and detail page URLs on the fly.

*   **Host Names:** The `activeSwitchNames` array at the top of the `<script>` tag is the only thing that needs to be configured.
*   **URL Generation:** The script constructs the necessary URLs by combining a base path with the host name, the selected metric (`if_bytes` or `uptime`), and the selected time period (`day`, `week`, etc.).
*   **Transparent Overlay:** The "transparent" graph effect is achieved with a single, highly performant CSS property: `mix-blend-mode: multiply;`. This browser feature blends the layers, treating white as transparent, without any need for complex image processing.

## Usage

1.  Download the `index.html` file.
2.  Open the file in a text editor.
3.  Locate the `activeSwitchNames` JavaScript array near the top of the `<script>` block.
4.  Replace the contents of this array with your own list of hostnames from your Munin setup.
5.  Save the file and open it in a web browser. It can be served from a web server or opened directly from your local filesystem.
