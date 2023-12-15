# Backface Detection
- Assume solid (close / water-tight) objects constructed from polygons
- Assumes each polygon norm is pointing outwards
## Algorithm
$n$ is the norm and $v$ is the vector from the camera to the polygon
- If the norm is pointing away from the camera, the polygon is not visible
    - $n \cdot v \geq 0$ 
- If the norm is pointing towards the camera, the polygon is visible
    - $n \cdot v < 0$<br>

# Depth Buffer
0. Reject back-facing polygons
1. Initialize depth buffer to $-\infty$ / $Z_far$<br>
Initialize frame buffer: background color
2. Process each triangle
    - For each pixel (x,y) in the triangle calculate z
    - If z < depth buffer at (x, y) in frame buffer
        - Update frame buffer at (x, y) with color of triangle
        - Update depth buffer at (x, y) with z
After processing all triangles
- Depth buffer contains the depth of the closest object (smallest z) at each pixel
- Frame buffer contains the color of the closest point

# Triangle Mesh
## Rendering
### VBO
Stores all 3 vertices of a triangle
Cons:
- Redundant data
- Floating point error may make the same vertex different after rotation
### EBO
Stores only one copy of the vertices, using indices to refer to them when drawing

## Orientation
- Use CCW to list vertices
- Orientable: consistent "outward" direction
    - Outward normal = $(v_1 - v_0) \times (v_2 - v_0)$
- Shared edges should be traversed in opposite directions for adjacent faces (making the two triangles both CCW)