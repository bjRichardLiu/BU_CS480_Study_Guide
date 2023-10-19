# 2D Transformations
All transformations below are done in homogeneous coordinates.
## Translation
$$\begin{bmatrix}
1 & 0 & t_x \\
0 & 1 & t_y \\
0 & 0 & 1
\end{bmatrix}$$
## Scaling
$$\begin{bmatrix}
s_x & 0 & 0 \\
0 & s_y & 0 \\
0 & 0 & 1
\end{bmatrix}$$
**Side Note:**<br>
A more commonly used scaling is scale on only one direction, rather than always scale by the origin.<br>
$$T_{out} S T_{in}p = p'''$$
Note the order is from right to left, i.e. $T_{in}$ is applied first (translate to origin), then $S$(scale), and finally $T_{out}$(translate back to the target position).<br>
It's also a good idea to combine $T_{out} S T_{in}$ first, then apply to p.<br>

## Inverse Transformation
$$M^{-1}M = I$$
Can easily reverse any transformation using its inverse matrix.<br>

## Mirror
### Mirror on x-axis
$$\begin{bmatrix}
1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 1
\end{bmatrix}$$
### Mirror on y-axis
$$\begin{bmatrix}
-1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}$$
### Mirror on y = x
$$\begin{bmatrix}
0 & 1 & 0 \\
1 & 0 & 0 \\
0 & 0 & 1
\end{bmatrix}$$

## Euler Rotation
### Rotation Matrix 
CCW about origin by $\theta$ radians
$$R = \begin{bmatrix}
\cos \theta & -\sin \theta & 0 \\
\sin \theta & \cos \theta & 0 \\
0 & 0 & 1
\end{bmatrix}$$
Note that R is orthonormal, thus its transpose is its inverse.<br>
Inverse are generally expensive to compute, but transpose is very easy.<br>

## Shearing
### Shearing on x-axis
$$\begin{bmatrix}
1 & \alpha & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}$$
### Shearing on y-axis
$$\begin{bmatrix}
1 & 0 & 0 \\
\beta & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}$$
Note that if $\alpha$/$\beta$ is positive, then the shearing is to the right/up, otherwise to the left/down.<br>

## Rotation about an arbitrary point
TODO
$$M = T_{out}R_{out}SR_{in}T_{in}$$

## Homogenous Coordinates
TODO