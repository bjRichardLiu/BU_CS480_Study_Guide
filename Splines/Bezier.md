# Cubic Bezier Curve
- 4 control points
- Interpolates p(0) to p(1)
$$p(u) = \sum_{i = 0}^3 b_i^3(u) p_i$$
$$\text{where } b_i(u) = \binom{3}{i}u^i(1 - u)^{3 - i}$$
$$p(u) = (1 - u)^3 p_0 + 3(1 - u)^2 u p_1 + 3(1 - u) u^2 p_2 + u^3 p_3$$
## Convex Hull
- 4 control points
- curve goes through endpoints
    - p(0) = p0; p(1) = p3
- curve approximates other points
- Bezier curve is bounded by convex hull (smallest convex polygon)
## Alternative Form
$$p(u) = \begin{bmatrix}
u^3 & u^2 & u & 1
\end{bmatrix} M_{Bez}\begin{bmatrix}
p_0 \\
p_1 \\
p_2 \\
p_3
\end{bmatrix}$$
$$M_{Bez} = \begin{bmatrix}
-1 & 3 & -3 & 1 \\
3 & -6 & 3 & 0 \\
-3 & 3 & 0 & 0 \\
1 & 0 & 0 & 0
\end{bmatrix}$$
$$p(u) = (-u^3 + 3u^2 - 3u + 1) p_0 + (3u^3 - 6u^2 + 3u) p_1 + (-3u^3 + 3u^2) p_2 + u^3 p_3$$
### Linear
$$p(u) = (1 - u) p_0 + u p_1$$
# Piecewise Bezier Curve
- Multiple Bezier curves connected together
- Able to "fine tune" the curve locally
## C0 Continuity
- If they join at the same endpoint
    - $p(s_{max}) = q(t_{min})$
## C1 Continuity
- Requires C_0 continuity
- First derivatives match at the join
    - $p'(s_{max}) = q'(t_{min})$
### Tangent
$$\frac{d}{du}p(0) = 3(p_1 - p_0)$$
$$\frac{d}{du}p(1) = 3(p_3 - p_2)$$

## G1 Continuity
- Requires C_0 continuity
- Derivatives are in the same direction at the join
    - $p'(s_{max}) = k q'(t_{min})$ where $k$ is some scalar
- Points before and after the joint are collinear

## C2 Continuity
- Requires C_1 continuity
- Second derivatives match at the join
    - $p''(s_{max}) = q''(t_{min})$

## Hermite Constraints
- $p_k$ and $p_{k+1}$ are the endpoints
- $Dp_k$ and $Dp_{k+1}$ are the tangents
$$\begin{align*}
\text{curve}(0) &= p_k \\
\text{curve}(1) &= p_{k+1} \\
\text{curve'}(0) &= Dp_k \\
\text{curve'}(1) &= Dp_{k+1}
\end{align*}$$

$$\begin{align*}
curve(u) &= au^3 + bu^2 + cu + d
\text{curve}(0) &= d = p_k \\
\text{curve}(1) &= a + b + c + d = p_{k+1} \\
\text{curve'}(0) &= c = Dp_k \\
\text{curve'}(1) &= 3a + 2b + c = Dp_{k+1}
\end{align*}$$
### Matrix Form
$$\begin{bmatrix}
p_k \\
p_{k+1} \\
Dp_k \\
Dp_{k+1}
\end{bmatrix} = \begin{bmatrix}
d \\
a + b + c + d \\
c \\
3a + 2b + c
\end{bmatrix} = \begin{bmatrix}
0 & 0 & 0 & 1 \\
1 & 1 & 1 & 1 \\
0 & 0 & 1 & 0 \\
3 & 2 & 1 & 0
\end{bmatrix} \begin{bmatrix}
a \\
b \\
c \\
d
\end{bmatrix}$$
$$\begin{bmatrix}
a \\
b \\
c \\
d
\end{bmatrix} = A^{-1} \begin{bmatrix}
p_k \\
p_{k+1} \\
Dp_k \\
Dp_{k+1}
\end{bmatrix}$$
$$\text{curve}(u) = \begin{bmatrix}
u^3 & u^2 & u & 1
\end{bmatrix} \begin{bmatrix}
a \\
b \\
c \\
d
\end{bmatrix} = \begin{bmatrix}
u^3 & u^2 & u & 1
\end{bmatrix} A^{-1} \begin{bmatrix}
p_k \\
p_{k+1} \\
Dp_k \\
Dp_{k+1}
\end{bmatrix}$$
$$\text{where } A^{-1} = \begin{bmatrix}
2 & -2 & 1 & 1 \\
-3 & 3 & -2 & -1 \\
0 & 0 & 1 & 0 \\
1 & 0 & 0 & 0
\end{bmatrix}$$

# Surfaces using Bezier
Grid with $m + 1$ rows and $n + 1$ columns
$$\text{Bezier: } p(u, v) = \sum_{i = 0}^m \sum_{j = 0}^n p_{j \cdot k}B_j(v)B_k(u)$$
Normal:
$$n(u, v) = \frac{\partial}{\partial u} \times \frac{\partial}{\partial v}$$
$$\frac{\partial}{\partial u} = \sum_{j = 0}^m \sum_{k = 0}^n p_{j \cdot k}B_j(v)\frac{\partial}{\partial u}B_k(u)$$
$$\frac{\partial}{\partial v} = \sum_{j = 0}^m \sum_{k = 0}^n p_{j \cdot k}\frac{\partial}{\partial v}B_j(v)B_k(u)$$

# de Casteljau's Algorithm
- Used to find any u on a Bezier curve
- Take take points at u along each line segments




