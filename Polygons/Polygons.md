# Polygons
## Simple Polygon
- No holes
- No repeated vertices
- No intersecting edges
- 2 edges meet at each vertex
### Traversing polygon
for CCW polygon<br>
- "outside" always to right
- "inside" always to left
#### Polygon with holes
Vertices for holes given in CW order
## Right Hand Rule
Normal points out from polygon plane<br>
TODO: Needs more explanation<br>

## Concave vs Convex
Convex: 
- any line segment connecting two points in the polygon lies entirely inside the polygon
- all interior angles are $\leq$ 180 degrees

## Cross product
For CCW polygon
- if the angle is convex, then the cross product is positive (point out of the plane)
- if the angle is concave, then the cross product is negative (point into the plane)

## Inside-Outside Test
### Minimum Bounding Rectangle (MBR)
- Find the minimum and maximum x and y coordinates of the polygon
- If the point is outside the MBR, then it's outside the polygon
- If the point is inside the MBR, then more tests needed
### Even-Odd Parity Rule
- Choose a point strictly outside of the polygon
- Draw a line from the outside point to the test point
- Count the number of intersections with the polygon<br>
**Odd -> inside**<br>
**Even -> outside**
#### Problems
- The line intersect with the vertex of the polygon
- The line coincides with an edge of the polygon
**Basics Solution: Choose another outside point**
### Winding Number


