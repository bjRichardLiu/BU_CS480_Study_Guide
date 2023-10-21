# 3D Viewing Pipeline
## Idea
Just like taking a photo
- Camera position & orientation (Viewing origin)
- scene cropped to viewing window (clipping) <br>

But in Computer Graphics, we are more flexible than the real world

## Pipeline
- MC -> Modeling Transforms
- WC -> Viewing Transforms
- VS -> Projection Transform (project onto viewing plane using parallel or perspective projection)
- PC (Projection coordinates) -> Normalize Transformations
- NC Viewport Transformations
- DC (Device coordinates)
## Camera coordinate system
- Viewing origin (camera/eye position)
- Direction of viewing (camera $Z_{view}$-axis)
- View plane positioned on $Z_{view}$-axis
### Viewing Coordinate Reference Frame
TODO
## World coordinates to Viewing coordinates
1. Translate viewing origin to the world origin
$$T = \begin{bmatrix}
1 & 0 & 0 & -X_0\\
0 & 1 & 0 & -Y_0\\
0 & 0 & 1 & -Z_0\\
0 & 0 & 0 & 1
\end{bmatrix}$$
2. rotate viewing coordinate axes to align with world coordinate axes
$$R = \begin{bmatrix}
u_X & u_Y & u_Z & 0\\
v_X & v_Y & v_Z & 0\\
n_X & n_Y & n_Z & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$
$$M_{WC,VC} = RT = \begin{bmatrix}
u_X & u_Y & u_Z & -u_0^T \cdot P_0 \\
v_X & v_Y & v_Z & -v_0^T \cdot P_0 \\
n_X & n_Y & n_Z & -n_0^T \cdot P_0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$


