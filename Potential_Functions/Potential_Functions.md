# Spherical Potential (Quadratic)
Repulsive potential
## Pairwise Potential
$$f(p, q) = (q - p)^T(q - p) = (x_q - x_p)^2 + (y_q - y_p)^2 + (z_q - z_p)^2$$
p is rewarded for keeping maximum distance from q, repelled by q<br>
Take gradient to find the next step
$$\triangledown f(p, q) = \begin{bmatrix}
\frac{\partial f}{\partial x_p} \\
\frac{\partial f}{\partial y_p} \\
\frac{\partial f}{\partial z_p}
\end{bmatrix} = \begin{bmatrix}
2(x_q - x_p)(-1) \\
2(y_q - y_p)(-1) \\
2(z_q - z_p)(-1)
\end{bmatrix} = -2(q - p) = 2(p - q)$$
## Many Creatures
$$f_{tot} = \sum_{i = 1}^{n} f(p_i, q_i)$$
$$\triangledown _p f_{tot} = 2\sum_{i = 1}^{n} (p - q_i)$$
## Attraction
$$-\triangledown _p f(p, q) = 2(q - p)$$

# Gaussian Potential
Attractive potential

$$
\begin{align*}
f(p, q) &= e^{-||p - q||^2} \\
\triangledown _p f(p, q) &= 2(q - p)e^{-||p - q||^2}
\end{align*}$$

# Reciprocal Quadratic Potential
Attractive potential

$$\begin{align*}
f(p, q) &= \frac{1}{(p - q)^T(p - q) + \epsilon} \\
\triangledown _p f(p, q) &= \frac{2 (q - p)}{(||q - p||^2 + \epsilon)^2}
\end{align*}$$
where $\epsilon$ is a small constant to avoid division by zero