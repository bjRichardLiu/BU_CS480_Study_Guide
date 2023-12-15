# Illumination Models
## Ambient
- Equal, non-directional illumination
- Does not depend on light position, surface geometry / orientation or viewer position
### Equation
$$I_{ambient} = k_a I_a$$
where $k_a$ is the ambient reflection coefficient and $I_a$ is the ambient light intensity

## Diffuse
- Light reflected equally in all directions
- Depends on surface normal and light direction
- Does not depend on viewer position
### Equation
$$I_{diffuse} = k_d I_l (N \cdot L) \text{ for } (N \cdot L) > 0$$
where $k_d$ is the diffuse reflection coefficient, $I_l$ is the light intensity, $N$ is the surface normal, and $L$ is the light direction<br>
Note: $N \cdot L = \cos(\theta)$ of the angle between the normal and the light direction, if smaller than 0, meaning the light is shining on the back of the surface, then the surface is not illuminated

## Specular
- Intense "highlight" when light reflects off a shiny surface
- Depends on surface normal, light direction
- Depends on viewer position
### Equation
$$I_{specular} = k_s I_l (R \cdot V)^{ns} \text{ for } R \cdot V, N \cdot L > 0$$
$$R = 2(N \cdot L)N - L$$
where $k_s$ is the specular reflection coefficient, $I_l$ is the light intensity, $R$ is the reflection direction, $V$ is the viewer direction, and $n$ is the shininess coefficient<br>
Note: greater $ns$ means smaller highlight (a sudden drop)


# Light Sources
## Infinite Light
- Models light source from a very far distance
- Light ray is parallel to each other
- L constant does not depend on the position of the light, only the direction


## Radial Intensity Attenuation
- Light intensity decreases quadratically with distance
- $f_{radatten}(d_l) = \frac{1}{a_1 + a_2d_l + a_3d_l^2}$ where $d$ is the distance from the light source

## Point Light
- Light emitted from a single point
- Unit light vector $L$ is $p_sp_l$ (direction of the light, point of surface to point of light)
- $L = \frac{p_l - p_s}{||p_l - p_s||}$

## Spot Light
- Light emitted from a single point in a cone
- There is a cutoff angle $\theta$ where the light intensity is 0 outside of the cone
- There are both radial and angular attenuation for diffuse and specular
- $f_{angatten}(\theta) = (v_{obj} \cdot v_l)^{as} \text{ for } v_{obj} \cdot v_l > \cos(\theta _l)$ <br>where $v_{obj}$ is the vector from the object to the light source, $v_l$ is the direction of the light source, $as$ is the angular attenuation coefficient
    - smaller $as$ means more gradual dropoff, the spotlight is wider
    - greater $as$ means more sudden dropoff, the spotlight is narrower


# Combined Illumination Model
$$I = I_{ambient} + \sum_{l}I_{ldiffuse} + I_{lspecular}$$
$$I = min(1, I) \text{ Clamp the result to [0, 1]}$$

Adding different light sources
$$I = I_{ambient} + \sum_{l}f_{liradatten} \cdot f_{liangatten}(I_{ldiffuse} + I_{lspecular})$$

