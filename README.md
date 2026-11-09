# Turbofan Model and Inlet Shape CFD Study

A CAD model of a turbofan-style jet engine, plus a research project on one question:

**How does changing the inlet shape affect total-pressure loss at a measured flow rate?**

Status: in progress.

## CAD model

[CAD FILE](https://cad.onshape.com/documents/876682d754e29310e05e23c9/w/4c2a69ee31b7700c60235b06/e/81a0a1613ddd50efce8a70d9)
<img width="3504" height="2478" alt="Part Studio 1 (2)" src="https://github.com/user-attachments/assets/25f11997-959c-4c8c-aaf3-9a1126b4fbed" />
[CAD folder](/cad)

The engine was built by following a YouTube tutorial: https://www.youtube.com/watch?v=DE8bgbyb9xw


It is a display model of a turbofan: a fan at the front, a duct (nacelle) around a smaller core, and compressor, fuel, turbine and exhaust sections behind it. It is not a working engine design and has no real performance data.

## Research question and method

The study compares a few inlet shapes, changing one feature at a time (lip shape, lip size or inlet length), while keeping the fan-face diameter, hub size and airflow the same.

1. **Build the inlet shapes.** Sketch one profile in CAD, revolve it around the centerline, and keep every dimension named so one number can be changed per version. Subtract each shape from a large box of air to get the fluid space for CFD.
2. **Run CFD.** Steady, incompressible flow. Freestream speed on the box boundaries, mass flow rate set at the fan face, and the same settings for every shape. Start with a 2D axisymmetric slice if the software allows it.
3. **Check the results.** Run a mesh test (coarse, medium, fine), watch convergence of the loss value, and look at velocity and pressure along the inlet wall.

## What is measured
 
The main result is the total-pressure loss from the freestream (station 0) to the fan face (station 2). Here $p_{t,0}$ is the freestream total pressure and $\overline{p}_{t,2}^{\,m}$ is the mass-flow-weighted mean total pressure at the fan face.
 
Total-pressure loss and total-pressure recovery ($\Pi_{t,\mathrm{rec}} = 1$ means no loss):
 
$$\Delta p_t = p_{t,0} - \overline{p}_{t,2}^{\,m}, \qquad \Pi_{t,\mathrm{rec}} = \frac{\overline{p}_{t,2}^{\,m}}{p_{t,0}}$$
 
The mass-flow-weighted mean over the fan-face plane $A$ is:
 
$$\overline{p}_{t}^{\,m} = \frac{\displaystyle\int_A p_t\,\rho u_n\,\mathrm{d}A}{\displaystyle\int_A \rho u_n\,\mathrm{d}A}$$
 
where $p_t$ is the local total pressure, $\rho$ is the density, and $u_n$ is the velocity normal to the plane.
 
Normalised loss, for comparing different speeds:
 
$$q_0 = \tfrac{1}{2}\rho_0 U_0^2, \qquad \Lambda_t = \frac{\Delta p_t}{q_0}$$
 
where $\rho_0$ and $U_0$ are the freestream density and speed.
 
Static-pressure difference is a different quantity and is reported separately if used. Fan-face pressure contours are used to look at uneven flow. The maximum-minus-minimum pressure is only a descriptive number, not a standard distortion measure.
 
## Possible later steps
 
- A small suction wind tunnel (honeycomb, contraction, test section, diffuser, fan) to test printed inlets with a pitot tube and a pressure sensor, and compare with the CFD.
- Using public weather data (for example wind speed and temperature at altitude) to set realistic freestream conditions.
- Manufacturing a scale model in metal. Check wall thickness and tolerance rules first.
## Credits
 
Engine CAD based on the YouTube tutorial linked above. Inlet background: NASA Glenn Research Center, Beginner's Guide to Aeronautics, "Inlets".
 
