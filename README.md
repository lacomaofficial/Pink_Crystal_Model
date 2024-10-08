# Overview of the Project

I created an aesthetic 3D brain model to visualize the feature importance from my deep learning models, focusing on the connections between Regions of Interest (ROIs). This model showcases which brain connections are significant in my work, such as in brain decoding, ADHD prediction, and gender differences in connectivity.

# Visualization Strategy

I use a 3D brain surface model to illustrate the connections (edges) between brain regions (nodes), emphasizing their importance with color and size. The stronger the connection, the more significant the feature. 

### Input Data
I start with a dataset containing feature names and their importance scores. Each feature corresponds to a pair of connected ROIs, with the importance score reflecting how critical the connection is to my model.

### Transformation of Data
The first function, `transform_df(df)`, splits the feature names (formatted as `Marker1 - Marker2`) into two separate markers, `Marker1` and `Marker2`. It also renames the importance score column to "Correlation," even though it represents importance rather than strict statistical correlation.

# Code Breakdown

### Data Transformation with `transform_df`
- **Purpose:** Split feature names into two markers and rename the importance score to "Correlation."
- **Steps:**
  - Ensure the necessary columns (`'Feature Name'` and `'Importance Score'`) are present.
  - Split the `'Feature Name'` into `Marker1` and `Marker2`.
  - Drop the original `'Feature Name'` column and rename `'Importance Score'` to `'Correlation'`.

### 3D Brain Visualization with `visualize_white_connectome_with_surface_final`
This function handles the plotting of my brain connections.

- **Parameters:**
  - `df_sorted`: DataFrame containing marker pairs and their importance scores (renamed to "Correlation").
  - `coords`: The 3D coordinates of the brain regions (ROIs).
  - `marker_labels`: The labels for the brain regions.
  - `cmap_markers` and `cmap_edges`: Color maps for visualizing nodes and edges.

- **Steps:**
  1. **3D Surface Mesh:** I triangulate the brain surface using the Delaunay triangulation method, creating a mesh from nearby points (vertices) to form triangles that define the brain’s surface.
  2. **Markers (Nodes) for ROIs:** 
     - The size and color of each node depend on its importance score. I use `cmap_markers` to assign colors based on these scores.
     - Labels identify each brain region next to the markers.
  3. **Edges (Connections) Between ROIs:** 
     - The connections are represented as lines, with color and thickness corresponding to their importance. More important connections are more prominent.
  4. **Layout Customization:** 
     - I adjust the plot layout for clarity, using a white background and removing titles and axis labels for a clean look. Legends are included for both the brain surface and connections.
  5. **Interactive Plot:** 
     - The final plot is generated with Plotly, allowing for interaction (zooming, rotating, etc.) to explore the brain’s regions and connections. Hovering reveals markers and their correlation values.

# Visualizing Feature Importance

By mapping feature importance to brain region connections in a 3D model, I provide an intuitive and aesthetic way to understand which connections matter most in my work. For example, in a deep learning model predicting ADHD or decoding neural signals, this visualization highlights the most important brain connections, helping researchers and clinicians focus on key neural circuits.
![crystal piink](https://github.com/user-attachments/assets/23725653-ba5d-4788-8e96-dbe57b792c76)
