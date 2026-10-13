# Project status

**Status:** Work in Progress
**Public snapshot:** 13 October 2026
**Author:** Axel Abdel Rahamane Meghezzi

## Included now

- a 63-second MP4 demonstration;
- a representative preview image;
- a verified high level technical overview;
- this release boundary and roadmap.

## Held back from this snapshot

- application source still undergoing cleanup;
- personal paths and generated local state;
- user and third party 3D models;
- CFD jobs, meshes, fields and archived results;
- bundled runtimes and build outputs;
- native code pending a complete license and provenance review.

## Public source release gates

1. Remove machine specific paths and local identities.
2. Remove mandatory assumptions about private or third party vehicle assets.
3. Complete the license and provenance inventory for every distributed component.
4. Separate source from runtimes, generated bundles, job state and scientific results.
5. Add a small redistributable geometry fixture with a known provenance.
6. Re-run the automated test suite from the clean public checkout.
7. Document a reproducible benchmark case and its limitations.

## Roadmap

### Milestone 0: showcase

Publish the interface demonstration and describe the technical direction without distributing unaudited code or models. **Current milestone.**

### Milestone 1: clean source

Publish the browser interface, local service and tests after the release gates above pass.

### Milestone 2: reproducible example

Provide a redistributable watertight model, a bounded local case and replayable configuration.

### Milestone 3: validation work

Compare against suitable public benchmarks and report mesh sensitivity, convergence, domain effects and uncertainty.

## Scientific boundary

The video is a software demonstration. It is not evidence of aerodynamic accuracy, solver convergence, a certified mesh or a validated drag coefficient.
