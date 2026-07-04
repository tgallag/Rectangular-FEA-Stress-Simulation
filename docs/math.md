# Stress Math Notes

This page starts from the smallest pieces and builds toward the quantities compared against the ANSYS result.

## 1. Geometry

Use these symbols first. Fill in the exact units once the final model settings are locked.

| Symbol | Meaning | Current value |
| --- | --- | --- |
| $L$ | beam length | $6$ |
| $h$ | rectangle height | $2$ |
| $b$ | rectangle thickness/depth | TBD |
| $F$ | applied force | TBD |
| $E$ | Young's modulus | TBD |
| $\nu$ | Poisson's ratio | TBD |

The cross-sectional area is:

$$
A = b h
$$

## 2. Force to Average Stress

If a force is spread evenly over the cross-section, the simplest stress estimate is:

$$
\sigma = \frac{F}{A}
$$

This is the starting point. It gives an average normal stress, not the full stress concentration or bending distribution.

## 3. Bending Moment

If the rectangle behaves like a cantilever with a force applied near the free end, the bending moment increases toward the fixed end:

$$
M_{\max} = F L
$$

For a different loading setup, replace this with the correct moment equation.

## 4. Area Moment of Inertia

For a rectangular cross-section bending about its centroidal axis:

$$
I = \frac{b h^3}{12}
$$

The farthest distance from the neutral axis is:

$$
c = \frac{h}{2}
$$

## 5. Maximum Bending Stress

The bending stress relation is:

$$
\sigma_b = \frac{M c}{I}
$$

Substituting the rectangular-section values:

$$
\sigma_{b,\max} = \frac{6M_{\max}}{b h^2}
$$

## 6. Strain and Deflection Check

Linear elastic strain:

$$
\epsilon = \frac{\sigma}{E}
$$

Cantilever tip deflection for an end load:

$$
\delta_{\max} = \frac{F L^3}{3 E I}
$$

This is a simple hand-check, not a replacement for the finite-element solution.

## 7. Equivalent Stress

ANSYS equivalent stress usually refers to von Mises stress. For a full 3D stress state:

$$
\sigma_{vm} =
\sqrt{
\frac{
(\sigma_x-\sigma_y)^2+
(\sigma_y-\sigma_z)^2+
(\sigma_z-\sigma_x)^2+
6(\tau_{xy}^2+\tau_{yz}^2+\tau_{zx}^2)
}{2}
}
$$

For a mostly one-direction stress state, this often reduces approximately to:

$$
\sigma_{vm} \approx |\sigma|
$$

## 8. ANSYS Comparison

Fill this in after the final solve:

| Quantity | Hand estimate | ANSYS result | Difference |
| --- | ---: | ---: | ---: |
| Maximum equivalent stress | TBD | TBD | TBD |
| Maximum deformation | TBD | TBD | TBD |
| Location of max stress | fixed/support region expected | TBD | TBD |

