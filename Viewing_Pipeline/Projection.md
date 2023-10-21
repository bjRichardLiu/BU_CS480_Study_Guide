# Projection
## Parallel vs Perspective projection
- Parallel projection("impossible camera"): preserves relative size of objects, parallel lines remain parallel; used for engineering drawings like CAD
- Perspective projection("real world camera"): objects appear smaller as they move away from the viewer, parallel lines converge at a vanishing point; used for realistic rendering

## Parallel projection
### Orthogonal Projection Coordinates
Drop the z-coordinate (collapsed on the view plane)
$$M_{VC,PC} = \begin{bmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$

### Oblique-Parallel Projection Coordinates
Using similar triangles to project the z-coordinate (similar to shear transformation)
$$M_{VC,PC} = \begin{bmatrix}
1 & 0 & \frac{-V_{px}}{V_pz{}} & Z_{vp}\frac{V_{px}}{V_{pz}}\\
0 & 1 & \frac{-V_{py}}{V_pz{}} & Z_{vp}\frac{V_{py}}{V_{pz}}\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$

## Perspective projection
### Projection Reference Point (prp)
- The "hole" of the pinhole camera
- All "rays" of projection pass through prp
- The image on the view plane is upside down from reality

### Compute Projection of a Point p
$$\begin{bmatrix}
\frac{Z_{vp}}{Z} & 0 & 0 & 0\\
0 & \frac{Z_{vp}}{Z} & 0 & 0\\
0 & 0 & \frac{Z_{vp}}{Z} & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$
TODO: Homogeneous, general solution