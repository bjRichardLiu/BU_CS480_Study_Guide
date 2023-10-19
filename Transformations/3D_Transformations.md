# 3D Transformations
All transformations below are done in homogeneous coordinates.

## Translation
$$\begin{bmatrix}
1 & 0 & 0 & t_x \\
0 & 1 & 0 & t_y \\
0 & 0 & 1 & t_z \\
0 & 0 & 0 & 1
\end{bmatrix}$$
## Scaling
$$\begin{bmatrix}
s_x & 0 & 0 & 0 \\
0 & s_y & 0 & 0 \\
0 & 0 & s_z & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$

## Euler Rotation

### CCW about x-axis by $\theta$ radians
$$R_x = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos \theta & -\sin \theta & 0 \\
0 & \sin \theta & \cos \theta & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$

### CCW about y-axis by $\theta$ radians
$$R_y = \begin{bmatrix}
\cos \theta & 0 & \sin \theta & 0 \\
0 & 1 & 0 & 0 \\
-\sin \theta & 0 & \cos \theta & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$

### CCW about z-axis by $\theta$ radians
$$R_z = \begin{bmatrix}
\cos \theta & -\sin \theta & 0 & 0 \\
\sin \theta & \cos \theta & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$

**Order Matters!**
For Euler angles, it's important to rotate
in $$R_zR_yR_x$$
i.e. rotate x first, then y, then z.

## Problem
### Gimbal Lock
- When two axes are aligned, the rotation matrix will lose one degree of freedom.
- Orthonormal, $R^TR = I$
### Hard to rotate about arbitrary axis
Rotate to align with z, then rotate about z, then rotate back to original position.
$$p' = (R_yR_x)^-1R_z(R_yR_x)$$