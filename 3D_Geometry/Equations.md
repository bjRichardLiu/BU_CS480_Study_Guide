# Implicit vs. Parametric Equations
## Implicit Equations
- Scalar function
- Provides procedure to test if point is on line
    - $f(x',y') = 0$ means on line
- Form: $$f(x,y) = 0$$
## Parametric Equations
- Vector function
- maps free parameter to point on line
- Gives procedure to sample points on line
    - t = 0.5 gives point on line $(x_0, y_0) + 0.5(x_1 - x_0, y_1 - y_0)$
- Form: 
$$\begin{bmatrix}
x(t) \\
y(t)
\end{bmatrix} = \begin{bmatrix}
x_0 \\
y_0
\end{bmatrix} + t \begin{bmatrix}
x_1 - x_0 \\
y_1 - y_0
\end{bmatrix}
$$


# Sphere

## Implicit Equation
$$f(x, y, z) = x^2 + y^2 + z^2 - r^2$$
For sphere centered at point $(C_x, C_y, C_z)$ and $||p - c||^2 = r^2$
$$f(x, y, z) = (x - C_x)^2 + (y - C_y)^2 + (z - C_z)^2 - r^2$$
### Test if point is inside sphere
- If $f(x, y, z) < 0$, then point is inside sphere, it's same as $x^2 + y^2 + z^2 < r^2$
- If $f(x, y, z) = 0$, then point is on sphere, it's same as $x^2 + y^2 + z^2 = r^2$
- If $f(x, y, z) > 0$, then point is outside sphere, it's same as $x^2 + y^2 + z^2 > r^2$

## Parametric Equation
$$
p(\phi, \theta) = \begin{bmatrix}
x(\phi, \theta) \\
y(\phi, \theta) \\
z(\phi, \theta)
\end{bmatrix} = \begin{bmatrix}
r \cos \theta \sin \phi \\
r \sin \theta \sin \phi \\
r \cos \phi
\end{bmatrix}
\text{ for } -\frac{\pi}{2} \leq \phi \leq \frac{\pi}{2}, -\pi \leq \theta \leq \pi
$$
### Assign UV Texture Coordinates
$$(u - 0.5, v - 0.5) = (\frac{\theta}{2\pi}, \frac{\phi}{\pi})$$
e.g.
$$\begin{align*}
(u, v) = (0, 0) &\rightarrow (\theta, \phi) = (-\pi, -\frac{\pi}{2})\\
(u, v) = (1, 1) &\rightarrow (\theta, \phi) = (\pi, \frac{\pi}{2})
\end{align*}$$

# Ellipsoid
## Implicit Equation
$$f(x, y, z) = (\frac{x}{r_x})^2 + (\frac{y}{r_y})^2 + (\frac{z}{r_z})^2 - 1$$
## Parametric Equation
$$
p(\phi, \theta) = \begin{bmatrix}
x(\phi, \theta) \\
y(\phi, \theta) \\
z(\phi, \theta)
\end{bmatrix} = \begin{bmatrix}
r_x \cos \theta \sin \phi \\
r_y \sin \theta \sin \phi \\
r_z \cos \phi
\end{bmatrix}
\text{ for } -\frac{\pi}{2} \leq \phi \leq \frac{\pi}{2}, -\pi \leq \theta \leq \pi
$$


