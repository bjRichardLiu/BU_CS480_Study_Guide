# Line Rasterization

## Linear Interpolation
### Equation
$$p(t) = (1-t) p_0 + t p_1$$
### Usage
#### Linearly interpolate color
$$c(t) = (1-t) c_0 + t c_1$$
$$c(t) = c_0 + tv_c$$
#### Texture mapping
TODO

## Line Slope-intercept equation
### Basic idea
$$y = mx + b$$
$$m = \frac{\Delta y}{\Delta x} = \frac{y_1 - y_0}{x_1 - x_0}$$
## Digital Differential Analyzer (DDA)
### Basic idea
Sample line at discrete positions, determine pixels, i.e. 
increment x by 1, check the y value, then determine which pixel to color.<br>
### Problems
- Floating point operations are expensive
- Round-off errors accumulate

## Bresenham's Algorithm
### Basic idea
- Similar to DDA, but use integer rather than floating point operations. <br>
- If the previous pixel is on the line, then the next pixel is either on the line or the line above it. <br>
### Algorithm
$$D_{k+1} = D_k + 2 \Delta y - 2(\Delta x)(y_{k+1} - y_k)$$
If $D_{k+1} > 0$, the choose the pixel above, otherwise if $D_{k+1} < 0$ choose the pixel on the line. <br>
<br>
**Only works for $0 \leq m \leq 1$**
<br>
<br>
**Intuition:** <br>
If the previous pixel is on the line (i.e. $D_k < 0$), then the next pixel ($D_{k+1}$) will be more likely to be the one above (favor $D_{k+1} > 0$). Because $(y_{k+1} - y_k) = 0$, the current equation is
$$D_{k+1} = D_k + 2 \Delta y$$

If the previous pixel already goes up the line (i.e. $D_k > 0$), then the next pixel will be harder to be the one above (favor $D_{k+1} < 0$). Because $(y_{k+1} - y_k) = 1$, the current equation is
$$D_{k+1} = D_k + 2 \Delta y - 2(\Delta x)$$
Only if $\Delta y > \Delta x$ can make the $D_{k+1} > 0$! <br>

**Side Note:**<br>
$D_{k+1}$ can be equal to 0, you can decide which pixel to choose in this case. <br>
### Implement to all slopes
If $D_{k+1} < 0$, we increment $x$ by 1 unit (could be +1 or -1, needs to be determined before hand), if $D_{k+1} > 0$, we increment $y$ by 1 unit. <br>
(For other ways, see [@36](https://piazza.com/class/ll1fg6tzvew83/post/36))

## Anti-aliasing
Divide each pixel into sub-pixels, and color each sub-pixel with the a mixed color of the line and the background. <br>
Use Bresenham's algorithm to determine how many columns of sub-pixels the line intersect in the current pixel. <br>
e.g., for AAlevel 4<br>
0: keep buffer color<br>
1: 1/4 line color + 3/4 buffer color<br>
2: 2/4 line color + 2/4 buffer color<br>
3: 3/4 line color + 1/4 buffer color<br>
4: keep line color<br>
<br>
**Side Note:**
Blend line color and background color can also be used for transparency. <br>