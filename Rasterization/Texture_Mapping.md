# Texture Mapping
- Paint objects with images, can be easily changed
- Use image to create the illusion of surface detail and complex geometry
- Simulate shadow
## Texture Maps
A 2D image that is mapped onto a 3D object<br>
Each pixel is referred to as "texel"

## Map Texture to Polygon
### Take the floor
Find the closest texel in texture map
#### Problem
If the polygon is bigger than the texture map, the same texel will be used multiple times, which will cause the blocks and staircases

### Bilinear Interpolation
Use the four closest texels to determine the color of the current pixel

### Texture Minification
- Use the average color of the texels onto each pixel (going the other way around)
- Also referred to as "downsampling" or "aliasing"<br>
Side note: one of the way to efficiently make pixel art assets

### Mipmapping
"Multum in parvo" - "much in little"<br>
- Use multiple texture maps to represent the same object
- Store them on the same texture map
- Choose the best resolution one to use based on the distance between the object and the camera