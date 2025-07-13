# Interactive Munin Layout

This project provides a modern, interactive single-page layout for viewing Munin-generated graphs. It transforms the default static HTML table into a responsive, filterable, and multi-metric analysis tool, making it significantly easier to navigate and correlate data from a large number of hosts.

It's a single, self-contained `index.html` file that can be dropped into any web server or opened locally.

## Features

*   **Immersive, Graphs-First View:** The page loads with a clean, uncluttered grid of graphs. All controls are hidden until needed.
*   **Comprehensive Keyboard-First Controls:**
    *   **Filter:** Start typing any letter to activate the filter bar. Supports both plain text and regular expressions.
    *   **Layout:** Press <kbd>1</kbd> - <kbd>9</kbd> to instantly set the number of columns.
    *   **Graph Type:** Press <kbd>T</kbd> for Traffic graphs or <kbd>U</kbd> for Uptime.
    *   **Time Period:** Press <kbd>D</kbd>, <kbd>W</kbd>, <kbd>M</kbd>, or <kbd>Y</kbd> for Day, Week, Month, or Year views.
    *   **Overlay Mode:** Press <kbd>O</kbd> to toggle the graph overlay comparison mode.
    *   **Help:** Press <kbd>?</kbd> to view all keyboard shortcuts.
    *   **Close:** Press <kbd>Esc</kbd> to close the filter bar or help screen.
*   **Multi-Metric and Multi-Period Views:** All controls are available in the header for mouse users.
*   **Advanced Overlay Comparison Mode:**
    *   **Blended View:** Toggling "Overlay" mode stacks all currently filtered graphs, using CSS `mix-blend-mode` to make their white backgrounds transparent. This creates a powerful composite view for spotting outliers and correlations.
    *   **Isolate on Hover:** Below the blended graph, a list of all active switches appears. Hovering your mouse over any switch name in the list instantly isolates its graph, making it fully opaque for clear inspection.
*   **Zero Dependencies & Easy Setup:**
    *   The entire application is a **single, self-contained `index.html` file**.
    *   Written in vanilla HTML, CSS, and JavaScript. No build process or server-side code is required.

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
