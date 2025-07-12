# Interactive Munin Layout

This project provides a modern, interactive single-page layout for viewing Munin-generated graphs. It replaces the default static HTML table with a responsive, filterable grid, making it significantly easier to navigate and analyze a large number of system monitoring graphs.

It's designed to be a drop-in replacement or a standalone viewer that leverages the predictable URL structure of a Munin installation.



## The Problem

The default Munin web interface, while functional, is a static HTML page that becomes difficult to use when monitoring dozens or hundreds of devices. Finding a specific graph requires manually scrolling and scanning a large, fixed table. This project aims to solve that by providing a fast, modern, client-side interface for the same data.

## Features

*   **Graphs-First Immersive View:** Loads with a clean, uncluttered grid of graphs. The controls are hidden until needed.
*   **Instant "Type-to-Filter" Search:** Simply start typing any character to bring up the filter bar. The grid updates instantly as you type, supporting both plain text and regular expressions.
*   **Time Period Selector:** Easily switch between `Day`, `Week`, `Month`, and `Year` views. The graph images update on the fly.
*   **Dynamic Zoom & Reflow:** An intuitive slider allows you to zoom in or out, and the grid automatically adjusts the number of columns to best fit your screen and zoom level.
*   **Commented Host Support:** Includes a data structure to recognize hosts that are commented-out in the original Munin config, displaying them as inactive.
*   **Zero Dependencies:** It's a single, self-contained `index.html` file written in vanilla HTML, CSS, and JavaScript. No build process or server is required.
*   **Predictable & User-Controlled:** The filter bar appears when you need it and is hidden with the `Esc` key or a close button. No unpredictable auto-hiding behavior.

## How It Works

The core of the project is a JavaScript array containing the names of the monitored hosts. It dynamically generates the graph and detail URLs based on Munin's standard URL structure:
`.../{HOST_NAME}/if_bytes-{PERIOD}.png`

This makes it easy to adapt to any Munin setup by simply editing the list of hostnames in the script.
