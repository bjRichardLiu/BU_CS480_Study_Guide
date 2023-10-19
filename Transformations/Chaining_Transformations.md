# Chaining Transformations
## Child rotation
Rotate by the local origin (rotation shoulder).
$$p' = M_1p$$
$$M_1 = T(c_1)R(\Theta _1)T(-c_1)$$

## Parent rotation
Parent:
$$p' = M_1p$$
Child:
$$p'' = M_2p' = M_2M_1p$$
**Intuition**<br>
Rotate the child local origin first ($M_1$), then rotate the child($M_2$).
$$c_1' = M_2c_1$$

## Tree to Store Hierarchy
TODO