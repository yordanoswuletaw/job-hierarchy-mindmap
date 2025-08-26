# Job Hierarchy Mind Map Visualization

A complete web application that visualizes job hierarchies as an interactive mind map using D3.js.

## Features

- **Interactive Mind Map**: Radial tree layout with the virtual root "Job Roles" at the center
- **Collapsible Nodes**: Click any node to expand/collapse its child branches
- **Zoom & Pan**: Scroll to zoom, drag to pan across the visualization
- **Tooltips**: Hover over nodes to see full job titles
- **Responsive Design**: Automatically adjusts to window size
- **Modern UI**: Beautiful gradient background with smooth animations

## Data Structure

The application expects a `job_title_graph.json` file with the following structure:

```json
{
  "source_nodes": ["Information Technology", "Healthcare & Life Sciences", ...],
  "adjacency_list": {
    "Information Technology": ["Software Development", "Cybersecurity", ...],
    "Software Development": ["Front End Developer", "Back End Developer", ...],
    ...
  }
}
```

## How to Use

1. **Open the Application**: Open `index.html` in a modern web browser
2. **Navigate**: 
   - Scroll to zoom in/out
   - Drag to pan around the visualization
   - Click nodes to expand/collapse branches
3. **Controls**:
   - **Reset View**: Return to the original zoom level and position
   - **Expand All**: Show all job hierarchy levels
   - **Collapse All**: Hide all expanded branches

## Technical Details

- **Framework**: Vanilla JavaScript with D3.js v7
- **Layout**: Radial tree layout using `d3.tree()` and `d3.linkRadial()`
- **Data Processing**: Automatically creates a virtual root node and builds the hierarchy
- **Null Handling**: Treats null values in adjacency lists as terminal nodes with "[N/A]" labels
- **Responsive**: Automatically adjusts to window resizing

## Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## File Structure

```
jlot_vizualization/
├── index.html          # Main application file
├── job_title_graph.json # Job hierarchy data
└── README.md           # This file
```

## Data Loading

The application automatically loads data from `job_title_graph.json` when the page loads. If there's an error loading the data, an error message will be displayed with a retry option.

## Customization

You can easily customize the visualization by modifying the CSS variables and JavaScript functions:

- **Colors**: Modify the `getNodeColor()` function
- **Node Sizes**: Adjust the `getNodeRadius()` function  
- **Styling**: Update CSS classes for different visual themes
- **Layout**: Modify the tree layout parameters in `createVisualization()`

## Performance Notes

- The application efficiently handles large hierarchies by only rendering visible nodes
- Collapsible functionality helps manage complex job structures
- Smooth animations and transitions provide a polished user experience
