# 2D Viewing Pipeline
## Procedure
1. Modeling-Coordinate Transformations
2. Construct World-Coordinate Scene
3. Generate view from the scene
4. Normalize the coordinates
5. Clip the view and project to device coordinates
## Pipeline
- MC -> Construct world-coordinate scene
- WV -> Convert to viewing coordinates
- VS -> Normalize coordinates
- NC -> Map to device coordinates
- DC

$$M = M_{NC,DC}M_{VC,DC}M_{WC,VC}M_{MC,WC}$$