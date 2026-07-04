# Stress Math Notes

Values below were extracted from the ANSYS Workbench project `RecangularCubeBeam` and checked against the MAPDL result file.

## 1. Model Values

ANSYS uses MKS units internally.

| Symbol | Meaning | Value |
| --- | --- | ---: |
| $L$ | beam length along $y$ | $0.006\ \text{m} = 6\ \text{mm}$ |
| $w$ | cross-section width along $x$ | $0.002\ \text{m} = 2\ \text{mm}$ |
| $t$ | cross-section thickness along $z$ | $0.00125\ \text{m} = 1.25\ \text{mm}$ |
| $F_x$ | applied force on free end | $100\ \text{N}$ |
| $E$ | Young's modulus, structural steel | $200\ \text{GPa}$ |
| $\nu$ | Poisson's ratio | $0.30$ |

Boundary conditions:

- Fixed support on the $y = 0$ face
- Force applied on the $y = L$ face
- Force direction: $+x$

## 2. Cross-Section Area

$$
A = w t
$$

$$
A = (0.002)(0.00125) = 2.50 \times 10^{-6}\ \text{m}^2
$$

The average applied surface traction is:

$$
p = \frac{F}{A}
$$

$$
p = \frac{100}{2.50 \times 10^{-6}} = 4.00 \times 10^7\ \text{Pa} = 40\ \text{MPa}
$$

This matches the pressure value written in the ANSYS solver input.

## 3. Bending Moment

Treat the model as a cantilever beam for a first hand-check.

$$
M_{\max} = F L
$$

$$
M_{\max} = (100)(0.006) = 0.600\ \text{N}\cdot\text{m}
$$

## 4. Area Moment of Inertia

The beam axis is $y$. Since the force is in $x$, the beam bends about the $z$ axis.

$$
I_z = \frac{t w^3}{12}
$$

$$
I_z = \frac{(0.00125)(0.002)^3}{12}
= 8.33 \times 10^{-13}\ \text{m}^4
$$

The farthest distance from the neutral axis is:

$$
c = \frac{w}{2} = 0.001\ \text{m}
$$

## 5. Maximum Bending Stress

$$
\sigma_{b,\max} = \frac{M_{\max} c}{I_z}
$$

$$
\sigma_{b,\max} =
\frac{(0.600)(0.001)}{8.33 \times 10^{-13}}
= 7.20 \times 10^8\ \text{Pa}
= 720\ \text{MPa}
$$

This is a simple beam-theory estimate. It does not capture the full 3D stress concentration at the fixed face.

## 6. Tip Deflection Check

For a cantilever with an end load:

$$
\delta_{\max} = \frac{F L^3}{3 E I_z}
$$

$$
\delta_{\max} =
\frac{(100)(0.006)^3}{3(200 \times 10^9)(8.33 \times 10^{-13})}
= 4.32 \times 10^{-5}\ \text{m}
= 0.0432\ \text{mm}
$$

## 7. Equivalent Stress

ANSYS equivalent stress is von Mises stress:

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

For a mostly one-direction bending stress state, this is close to the bending stress magnitude:

$$
\sigma_{vm} \approx |\sigma_b|
$$

## 8. ANSYS Comparison

| Quantity | Hand estimate | ANSYS result | Difference |
| --- | ---: | ---: | ---: |
| Maximum equivalent stress | $720\ \text{MPa}$ | $861.3\ \text{MPa}$ | $+19.6\%$ |
| Estimated stress bound | $720\ \text{MPa}$ | $917.7\ \text{MPa}$ | $+27.5\%$ |
| Maximum deformation | $0.0432\ \text{mm}$ | $0.0475\ \text{mm}$ | $+10.0\%$ |

Result locations from the MAPDL result file:

- Maximum deformation: free end, node 671, near $(x,y,z)=(0,6,0.625)\ \text{mm}$
- Maximum equivalent stress: fixed face corner region, including nodes 547 and 592

The ANSYS values are higher than the simple hand check because the model is short relative to its cross-section and the fixed support creates a 3D stress concentration that beam theory does not fully capture.
