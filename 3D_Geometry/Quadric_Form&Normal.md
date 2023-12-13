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
## Example
- Sphere
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
- Ellipsoid
$$Q = \begin{bmatrix}
\frac{1}{r_x^2} & 0 & 0 & 0 \\
0 & \frac{1}{r_y^2} & 0 & 0 \\
0 & 0 & \frac{1}{r_z^2} & 0 \\
0 & 0 & 0 & -1
\end{bmatrix}$$
