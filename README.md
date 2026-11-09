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

The main result is total-pressure loss from the freestream (station 0) to the fan face (station 2):

```
Δp_t   = p_t,0 − p̄_t,2          total-pressure loss
Π_rec  = p̄_t,2 / p_t,0          total-pressure recovery (1 means no loss)
q_0    = ½ ρ_0 U_0²             freestream dynamic pressure
Λ_t    = Δp_t / q_0             normalised loss, for comparing different speeds
```

p̄_t,2 is the mass-flow-weighted mean total pressure over the fan-face plane:

```
p̄_t = ∫ p_t ρ u_n dA / ∫ ρ u_n dA
```

Static-pressure difference is a different quantity and is reported separately if used. Fan-face pressure contours are used to look at uneven flow. The maximum-minus-minimum pressure is only a descriptive number, not a standard distortion measure.

## Possible later steps

- A small suction wind tunnel (honeycomb, contraction, test section, diffuser, fan) to test printed inlets with a pitot tube and a pressure sensor, and compare with the CFD.
- Using public weather data (for example wind speed and temperature at altitude) to set realistic freestream conditions.
- Manufacturing a scale model in metal. Check wall thickness and tolerance rules first.

## Credits

Engine CAD based on the YouTube tutorial linked above. Inlet background: NASA Glenn Research Center, Beginner's Guide to Aeronautics, "Inlets".
