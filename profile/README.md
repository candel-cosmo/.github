# CANDEL

**CANDEL** is a GPU-accelerated hierarchical Bayesian framework for the local
distance ladder and peculiar velocities, built on JAX and NumPyro.

It is a small core library plus one repository per probe; each probe imports
the core and registers with it through the `candel.probes` entry point.

| Repository | Probe |
|---|---|
| [CANDEL](https://github.com/candel-cosmo/CANDEL) | Core: inference, selection integrals, field reconstructions, cosmography, job submission |
| [candel-pv](https://github.com/candel-cosmo/candel-pv) | Peculiar-velocity catalogues (TFR, FP, SNe), growth rate, S8 |
| [candel-ch0](https://github.com/candel-cosmo/candel-ch0) | Cepheid-calibrated H0 (SH0ES hosts) |
| [candel-trgb](https://github.com/candel-cosmo/candel-trgb) | TRGB-calibrated H0 (EDD) |
| [candel-mwcepheids](https://github.com/candel-cosmo/candel-mwcepheids) | Milky Way Cepheids |
| [candel-maser](https://github.com/candel-cosmo/candel-maser) | Megamaser disk distances and H0 |

Clone the probes you need next to `CANDEL`; see its README for installation.

- Documentation: [candel.readthedocs.io](https://candel.readthedocs.io)
- Contact: Richard Stiskalek (University of Oxford)
