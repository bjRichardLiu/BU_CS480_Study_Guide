# Quaternions
Rotate about an arbitrary axis in 3D space.<br>
## 3D Rotation Using Quaternions
$$q = (cos(\frac{\theta}{2}), u \ cdot sin (\frac{\theta}{2}))$$
where:<br>
$\theta$ is the angle of rotation<br>
$u$ is the unit vector of the axis of rotation<br>

## Matrix form
$$p'= Mp$$
$$M = \begin{bmatrix}
1 - 2b^2 - 2c^2 & 2ab - 2cs & 2ac + 2bs \\
2ab + 2cs & 1 - 2a^2 - 2c^2 & 2bc - 2as \\
2ac - 2bs & 2bc + 2as & 1 - 2a^2 - 2b^2
\end{bmatrix}$$
where:<br>
$q = (s, v)$<br>
$v$ = $(a, b, c)$<br>

## Chaining Rotations
$$p' = (q_2q_1)p(q_2q_1)^-1$$
**Generally not commutable**
### When does it commute?
- Case 1: $\theta = 0$
- Case 2: u is same (the rotation axis is the same)

