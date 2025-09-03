# Job Taxonomy Mind Map (Left-to-Right Tree)

An interactive, left-to-right mind map that visualizes a complete job taxonomy using D3.js. The layout uses a hierarchical tree where the root starts on the left and branches expand to the right.

## Features 

- **Left-to-Right Tree**: Root on the left (“Job Taxonomy”), branches grow to the right
- **Clear Levels**: Job Families → Job Functions → Roles → Specializations
- **Collapsible Branches**: Click any node to expand/collapse
- **Optional Grouping**: Large sibling sets are clustered alphabetically (A–C, D–F, …)
- **Zoom & Pan**: Scroll to zoom, drag to pan; reset anytime
- **Tooltips**: Hover to see full titles (labels stay concise)
- **Responsive**: Adapts to window resizing

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

1. **Open the Application**: Open `index.html` in a modern browser. If your browser blocks `fetch()` for local files, serve the folder with a static server (e.g., `python3 -m http.server`).
2. **Choose View**:
   - Select “All Job Families (Complete Taxonomy)” to see the full taxonomy with a virtual root “Job Taxonomy”.
   - Or choose a specific Job Family to focus that branch.
3. **Navigate**:
   - Scroll to zoom; drag to pan
   - Click nodes to expand/collapse
4. **Controls**:
   - **Reset View**: Restore baseline zoom and position
   - **Expand All**: Expand all branches
   - **Collapse All**: Collapse to the current root

## Technical Details

- **Framework**: Vanilla JavaScript with D3.js v7
- **Layout**: Left-to-right hierarchical tree using `d3.tree()` and `d3.linkHorizontal()`
- **Root**: Virtual root “Job Taxonomy” in full view; or a selected Job Family as the root
- **Levels**: Semantic levels control color/size (Families, Functions, Roles, Specializations)
- **Grouping**: Large sibling sets cluster into alphabetical buckets for scannability
- **Deduplication**: Duplicate edges within a sibling set are removed
- **Null Handling**: `null` children shown as terminal nodes labeled “[N/A]”
- **Responsive**: Automatically adjusts to window resizing

## Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## File Structure

```
jlot_vizualization/
├── index.html           # Main application (HTML+CSS+JS)
├── job_title_graph.json # Job hierarchy data (adjacency list + source_nodes)
└── README.md            # This file
```

## Data Loading

The application loads `job_title_graph.json` on page load. If loading fails, an error message is shown with a retry button.

## Customization

You can customize colors, sizes, and layout from code:

- **Colors**: Edit `getNodeColor()` (level-based palette)
- **Font Sizes**: Adjust `.label-level-*` classes in CSS
- **Node Sizes**: Edit `getNodeWidth()` and `getNodeHeight()`
- **Layout**: Change `NODE_H_SPACING`, `NODE_V_SPACING`, and `MARGIN`
- **Grouping**: Tweak `GROUP_THRESHOLD` and `GROUP_BUCKET_MAX`

## Performance Notes

- Renders only expanded branches for large hierarchies
- Deduplication reduces duplicate siblings from noisy inputs
- Alphabetical grouping keeps large levels scannable
