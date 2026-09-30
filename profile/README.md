# CANDEL

**CANDEL** is a GPU-accelerated hierarchical Bayesian framework for the local
distance ladder and peculiar velocities, built on JAX and NumPyro.

It is organised as a small core library plus one package per probe:

| Package | Probe |
|---|---|
| `candel` | Core: inference, selection integrals, field reconstructions, cosmography |
| `candel-pv` | Peculiar-velocity catalogues (TFR, FP, SNe), growth rate, S8 |
| `candel-ch0` | Cepheid-calibrated H0 (SH0ES hosts) |
| `candel-trgb` | TRGB-calibrated H0 (EDD) |
| `candel-mwcepheids` | Milky Way Cepheids |
| `candel-maser` | Megamaser disk distances and H0 |

New probes register with the core through the `candel.probes` entry point,
so adding one needs no change to the core.

- Code: [candel-cosmo/CANDEL](https://github.com/candel-cosmo/CANDEL)
- Contact: Richard Stiskalek (University of Oxford)
