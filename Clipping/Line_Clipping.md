# Line Clipping
Get rid of the part of the line that is outside the view window. <br>
## Cheap test: Bounding Box
If the point is outside the bounding box, then reject; else, render the point. <br>

## Cohen-Sutherland Line Clipping
### Idea
- Assign a 4-bit code to 9 regions (8 regions outside the window, 1 region 0000 inside the window)
- If both 0000 -> trivial accept
- If not 0000, use top (1000), bottom (0100), left (0010), right (0001) to clip the line, until end point becomes 0000 or both end points are in the same region (trivial reject)
TODO: add image & more explanation