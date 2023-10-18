# Triangle Rasterization
Basic component of more complex shapes, very commonly used in computer graphics, and relatively simple to render.<br>
## Flat Triangle Scan Fill
Fill the triangle from bottom to top, keep the y value, and increment x value by 1 unit. <br>
After coloring this line, increment y value by 1 unit, and repeat the process. <br>
## General Triangle Scan Fill
Problem: Transition not very easy to compute. <br>
Cut the triangle in half by the middle point, and fill the two flat triangles separately. <br>
## Linearly Interpolate
$$c(t) = (1-t) c_0 + t c_1$$
## Bilinear Interpolation
Do a linear interpolation on the two edges, and then do another linear interpolation on the targeted y value. <br>
TODO: add picture