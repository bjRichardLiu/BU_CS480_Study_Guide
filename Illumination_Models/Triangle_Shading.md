# Flat Shading
- Constant color for each triangle
- Unit normal to triangle N, apply illumination equation once per triangle using N
- Treat $N \cdot L$ and $V \cdot R$ as constant over triangle

# Gouraud Shading
- Interpolate vertex normals to get normals at each pixel
- Apply illumination equation at each pixel
- Smooth shading using bilinear interpolation
## Problem
- Specular highlights are not smooth and sharp

# Phong Shading
- Interpolate vertex normals to get normals at each pixel (instead of color)
- Apply illumination equation at each pixel
- Better approximates of non-linear parts of the illumination equation
- More expensive than Gouraud shading
