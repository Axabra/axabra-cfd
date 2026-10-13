# Technical overview

This document describes the verified structure of the current local AXABRA CFD development build. The implementation is still undergoing a public release and licensing audit, so this repository does not yet contain the application source.

## Data flow

```text
3D geometry
    |
    v
local import and geometry checks
    |
    v
local CFD job and OpenFOAM case
    |
    v
OpenFOAM under Ubuntu/WSL
    |
    v
local field extraction and storage
    |
    v
browser based 3D visualization
```

All project data and solver work are intended to remain on the local machine.

## 1. Browser interface

The front end uses JavaScript and Three.js to display vehicle geometry, wind tunnel context, scalar colour maps, smoke or streamline views and mesh information. Display controls change the presentation of an existing result; they do not silently recalculate the fluid solution.

## 2. Local service

A Node.js service binds to the local host and coordinates project storage, geometry uploads, job state, result streaming and media export. New CFD calculations are delegated to the installed local solver environment rather than to a remote service.

## 3. Geometry gate

Geometry is checked before a CFD job is created. The current development pipeline checks complete triangles, finite coordinates, topology and closure, and applies explicit size limits. Original and prepared geometry remain separate so that repairs do not overwrite the source model.

A watertight surface is a computational requirement, not a cosmetic detail. Open edges, duplicated faces, inverted normals, self intersections or missing surfaces can invalidate meshing even when the model looks correct in a renderer.

## 4. Solver workflow

The calculation path uses OpenFOAM through Ubuntu/WSL. Case preparation, meshing, solver execution and result extraction are separate stages with recorded job state. The local build also contains exploratory preview methods, but preview output is not treated as equivalent to a validated OpenFOAM calculation.

## 5. Weyl aware research layer

The research layer uses the representation

```text
Q = dphi
g_hat = exp(2 phi) g
```

with a corresponding pressure renormalization. In the current project this is an explicit representation and diagnostic layer. It does not by itself validate a CFD solution or replace mesh, convergence and benchmark checks.

## 6. Result interpretation

Credible CFD results require more than a successful solver exit. The project roadmap therefore calls for public benchmark cases, mesh sensitivity studies, domain and blockage checks, convergence evidence and reproducible solver settings before engineering claims are made.

The included video demonstrates the interface and visualization only.
