# Projection
## Parallel vs Perspective projection
- Parallel projection("impossible camera"): preserves relative size of objects, parallel lines remain parallel; used for engineering drawings like CAD
- Perspective projection("real world camera"): objects appear smaller as they move away from the viewer, parallel lines converge at a vanishing point; used for realistic rendering

## Affine Transformations
- Preserve parallelism
- Preserve ratios of distances along a line
- Preserve straight lines
**Scale, Rotate, Translate, Mirror, Shear**

## Parallel projection
**Affine Transformations**
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
**Not Affine Transformations**
### Projection Reference Point (prp)
- The "hole" of the pinhole camera
- All "rays" of projection pass through prp
- The image on the view plane is upside down from reality

### Compute Projection of a Point p
Using similar triangles
$$\frac{X_{vp}}{Z_{vp}} = \frac{X_p}{Z_p}$$
$$X_p = X(\frac{Z_{vp}}{Z})$$
where
- $X_{vp}$ is the x-coordinate of the point in the view plane
- $X_p$ is the x-coordinate of the point in the world coordinate
- $Z_{vp}$ is the z-coordinate of the point in the view plane
- $Z_p$ is the z-coordinate of the point in the world coordinate

We get
$$X_p = X(\frac{Z_{vp}}{Z})$$
$$Y_p = Y(\frac{Z_{vp}}{Z})$$
$$Z_p = Z_{vp} = Z$$
$$W_p = \frac{Z}{Z_p} = 1$$



$$\begin{bmatrix}
\frac{Z_{vp}}{Z} & 0 & 0 & 0\\
0 & \frac{Z_{vp}}{Z} & 0 & 0\\
0 & 0 & \frac{Z_{vp}}{Z} & 0\\
0 & 0 & 0 & 1
\end{bmatrix}$$

$$\begin{bmatrix}
X(\frac{Z_{vp}}{Z})\\
Y(\frac{Z_{vp}}{Z})\\
Z_{vp}\\
1
\end{bmatrix}$$

Homogenization -> divide by w<br>
$(x, y, z, w)$ -> $(\frac{x}{w}, \frac{y}{w}, \frac{z}{w}, 1)$<br>

### More General Solution
$$X_p = X(Z_{prp} - Z_p) + X_{prp}(Z_{vp} - Z)$$
$$Y_p = Y(Z_{prp} - Z_p) + Y_{prp}(Z_{vp} - Z)$$
$$Z_p = Z_{vp}(Z_{prp} - Z)$$
$$W_p = Z_{prp} - Z$$

