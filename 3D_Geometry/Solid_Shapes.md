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
# Quadric Form for Implicit Equation
- Quadric surfaces are described using quadratics
- Quadric form is a symmetric matrix Q
$$ p^TQp = 
\begin{bmatrix}
x & y & z & 1
\end{bmatrix}
\begin{bmatrix}
A & B & C & D \\
B & E & F & G \\
C & F & H & I \\
D & G & I & J
\end{bmatrix}
\begin{bmatrix}
x \\
y \\
z \\
1
\end{bmatrix}
$$
$$f(x, y, z) = Ax^2 + 2Bxy + 2Cxz + 2Dx + Ey^2 + 2Fyz + 2Gy + Hz^2 + 2Iz + J$$

# Normal
- Partial derivatives
- Cross product
## Implicit Equation
$$ n(x, y, z) = \triangledown f(x, y, z) = \begin{bmatrix}
\frac{\partial f}{\partial x} \\
\frac{\partial f}{\partial y} \\
\frac{\partial f}{\partial z}
\end{bmatrix}
$$
## Parametric Equation
$$ n(\phi, \theta) = \frac{\partial p}{\partial \phi} \times \frac{\partial p}{\partial \theta}$$

## Quadric
$$\begin{align*}
p^TQp &= 0 \\
n(p) &= \triangledown(p^TQp) \\
&= 2Qp
\end{align*}$$



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

## Quadric Form
$$Q = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & -r^2
\end{bmatrix} = \begin{bmatrix}
\frac{1}{r^2} & 0 & 0 & 0 \\
0 & \frac{1}{r^2} & 0 & 0 \\
0 & 0 & \frac{1}{r^2} & 0 \\
0 & 0 & 0 & -1
\end{bmatrix}$$

## Normal
### Implicit Equation
$$n(x, y, z) = \triangledown f(x, y, z) = \begin{bmatrix}
\frac{\partial f}{\partial x} (x^2 + y^2 + z^2 - r^2)\\
\frac{\partial f}{\partial y} (x^2 + y^2 + z^2 - r^2)\\
\frac{\partial f}{\partial z} (x^2 + y^2 + z^2 - r^2)
\end{bmatrix} = \begin{bmatrix}
2x \\
2y \\
2z
\end{bmatrix}$$
### Parametric Equation
$$n(\phi, \theta) = \frac{\partial p}{\partial \phi} \times \frac{\partial p}{\partial \theta} = \begin{bmatrix}
-r \sin \phi \cos \theta \\
-r \cos \phi \sin \theta \\
r \cos \phi
\end{bmatrix} \times \begin{bmatrix}
-r \cos \phi \sin \theta \\
r \cos \phi \cos \theta \\
0
\end{bmatrix}
$$
After normalization
$$\frac{n(\phi, \theta)}{||n(\phi, \theta)||} = \begin{bmatrix}
\cos \phi \cos \theta \\
\cos \phi \sin \theta \\
\sin \phi
\end{bmatrix}$$



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
## Quadric Form
$$Q = \begin{bmatrix}
\frac{1}{r_x^2} & 0 & 0 & 0 \\
0 & \frac{1}{r_y^2} & 0 & 0 \\
0 & 0 & \frac{1}{r_z^2} & 0 \\
0 & 0 & 0 & -1
\end{bmatrix}$$

# Cylinder
Top and bottom are just circles, the equation below is for the side
## Implicit Equation
Top view / segment of each layer along z-axis is a circle
$$f(x, y, z) = x^2 + y^2 - r^2 = (\frac{x}{r})^2 + (\frac{y}{r})^2 - 1$$
## Parametric Equation
$$
p(\theta, u) = \begin{bmatrix}
x\\
y\\
z
\end{bmatrix} = \begin{bmatrix}
r \cos \theta \\
r \sin \theta \\
u
\end{bmatrix}
\text{ for } -\pi \leq \theta \leq \pi, u_min \leq u \leq u_max
$$
## Quadric Form
$$Q = \begin{bmatrix}
\frac{1}{r^2} & 0 & 0 & 0 \\
0 & \frac{1}{r^2} & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & -1
\end{bmatrix}$$

# Cone
Radius change with z
## Implicit Equation
$$f(x, y, z) = x^2 + y^2 - (rz)^2 = (\frac{x}{rz})^2 + (\frac{y}{rz})^2 - 1$$
## Parametric Equation
$$
p(\theta, u) = \begin{bmatrix}
x\\
y\\
z
\end{bmatrix} = \begin{bmatrix}
r u \cos \theta \\
r u \sin \theta \\
u
\end{bmatrix}
\text{ for } -\pi \leq \theta \leq \pi, u_min \leq u \leq u_max
$$
## Quadric Form
$$Q = \begin{bmatrix}
\frac{1}{r^2} & 0 & 0 & 0 \\
0 & \frac{1}{r^2} & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 0
\end{bmatrix}$$

# Torus
## Implicit Equation
Drawing circle with radius $r$ around $z$-axis, centered at $r_{axial}$
$$f(x, y, z) = (\sqrt{x^2 + y^2} - r_{axial})^2 + z^2 - r^2$$
## Parametric Equation
$$
p(\phi, \theta) = \begin{bmatrix}
x\\
y\\
z
\end{bmatrix} = \begin{bmatrix}
(r_{axial} + r \cos \phi) \cos \theta \\
(r_{axial} + r \cos \phi) \sin \theta \\
r \sin \phi
\end{bmatrix}
\text{ for } -\pi \leq \theta, \phi \leq \pi
$$


