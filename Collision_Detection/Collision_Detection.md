# Bounding Boxes
## Axis-Aligned Bounding Boxes (AABBs)
- AABBs are the simplest type of bounding box
- Uses the minimum and maximum points of the box
### Detection
Check if x and y both overlap
$$(x_{min2} \geq x_{min1} \text{ \&\& } x_{min2} \leq x_{max1}) \text{ || } (x_{min1} \geq x_{min2} \text{ \&\& } x_{min1} \leq x_{max2})$$
$$(y_{min2} \geq y_{min1} \text{ \&\& } y_{min2} \leq y_{max1}) \text{ || } (y_{min1} \geq y_{min2} \text{ \&\& } y_{min1} \leq y_{max2})$$
### Problems
- AABBs are not very accurate, the box may be much larger than the object

## Oriented Bounding Boxes (OBBs)
- OBBs are AABBs that are rotated to fit the object
### Detection
1. Transform $OBB_1$ in canonical form
$$R_1 = \begin{bmatrix}
- & u_1^T & - & 0\\
- & v_1^T & - & 0\\
- & w_1^T & - & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$
$$T_1 = T(-C_1)$$
where $C_1$ is the lower corner of OBB_1
$$S_1 = S(\frac{1}{w_1}, \frac{1}{h_1}, \frac{1}{d_1})$$
where $w_1, h_1, d_1$ are the width, height, and depth of $OBB_1$
$$M_1 = S_1R_1T_1$$
For 8 corners $p_i$ of $OBB_2$, test if  $OBB_2p_i$ is inside $M$
$$0 \leq Mp_i \leq 1$$
2. Repeat step 1 for $OBB_1$ and $OBB_2$ swapped
3. Use Sutherland-Hodgman algorithm to test if $OBB_1$ and $OBB_2$ overlap, if no polygon is left, then they do not overlap, otherwise they do
#### Alternative Ways
- If no collision, there must exist a plane that separates the two objects
- Project the objects to perpendicular axes, if the projections do not overlap, then there is no collision

# Bounding Spheres
For two objects, with centers $C_1$ and $C_2$ and radii $r_1$ and $r_2$<br> 
$d = ||C_1 - C_2||$ <br>
if $d > r_1 + r_2$, then there is no collision
## Ritter's Algorithm
- A way to find the approximate bounding sphere
1. Find points with minimum and maximum x, y, and z coordinates
2. Find the two points with the maximum distance, initialize the center C with the midpoint of the two points, and initialize the radius r with half the distance
3. Check all points in the object, if point S is outside the sphere, expand the sphere to include the point
$$\begin{align*}
r' &= \frac{1}{2}(||S - C|| - r) + r \\
C' &= C + \frac{S - C}{||S - C||}(r' - r)
\end{align*}$$
# Hierarchical Bounding Structures
- A way to reduce the number of objects to test for collision
- Divide the space into a tree of bounding boxes, test bigger boxes first, if they collide, test the smaller boxes inside
- Spatial data structure: quad tree, oct-tree

# Image-Space Collision Detection
Use OpenGL stencil buffer to detect collision (test by drawing)
## 2D
- Clear stencil buffer to 0
- Draw object 1 to stencil buffer with bit 1
- Draw object 2 to stencil buffer with bit 2
- If any pixel has both bits 1 and 2, then there is a collision
## 3D
- Use orthographic projection
- Draw scene from x, y, z directions
- Clear stencil buffer to 0
- Draw object 1 to stencil buffer with bit 1
- Draw object 2 to stencil buffer with bit 2
- If bits set in all 3 directions, there is likely a collision