# Polygon Clipping
## Sutherland-Hodgman Polygon Clipping
- Consider each edge of the viewports individually
- For each edge, clip the polygon against that edge

### Algorithm
- Traverse through the view window edges, if meet an intersection with the polygon, then add the intersection point to the output polygon, and get rid off the part outside
- Input Polygon -> clip top -> clip bottom -> clip right -> clip left -> Output Polygon
#### 4 cases
- Leaving clip region $p_0 -- q -->p_1$: add $q$ to output polygon
- Entering clip region $p_1 <-- q --p_0$: add $q$ and $p_1$ to output polygon
- Inside clip region $p_0 --> p_1$: add $p_1$ to output polygon
- Outside clip region $p_0 <-- p_1$: do nothing
### Advantage
Boundary clipping routines can be implemented semiautomatically

### Problems
Concave polygons can be clipped incorrectly<br>
e.g., the accepted polygon is connected with one or more thin line(s)

## Weiler-Atherton Polygon Clipping
### Idea
- Traverse the polygon and the clip window, to find enclosed regions
- Each enclosed region is independent of the others
### Algorithm
- Determine which intersection nodes are entering (pointing into the viewing window) and which are leaving (pointing out of the viewing window)
- Start at an entering node
- If encounter an entering point, go to the polygon vertex
- If encounter a leaving point, go to the clip vertex
- Finish when you return to the starting point
- Repeat until visited all vertices
TODO: add image & more explanation


