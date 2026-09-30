# CANDEL

**CANDEL** is a GPU-accelerated hierarchical Bayesian framework for the local
distance ladder and peculiar velocities, built on JAX and NumPyro. It
forward-models distance indicators from geometric megamaser anchors through
Cepheids and TRGB to peculiar-velocity tracers, and infers $H_0$, $S_8$ and
velocity-field parameters directly from the data.

## How the repositories work

CANDEL is a core library plus one repository per probe.

- **[CANDEL](https://github.com/candel-cosmo/CANDEL)** is the core: inference
  (NUTS, evidence), selection integrals, field reconstructions, cosmography,
  run scripts and job submission, the documentation, and the shared `data/`,
  `results/` and `local_config.toml`.
- **Probe packages** import the core; the core never imports them. Each one
  registers a `candel.Probe` under the `candel.probes` entry point, and the
  core's `main.py` picks it up from the config's `model.which_run` once the
  package is installed.
- Clone the probes you need **next to** `CANDEL`; they read data and results
  from that checkout.

| Repository | Probe | `model.which_run` |
|---|---|---|
| [candel-pv](https://github.com/candel-cosmo/candel-pv) | Peculiar-velocity catalogues (TFR, FP, SNe), growth rate, S8 | unset |
| [candel-ch0](https://github.com/candel-cosmo/candel-ch0) | Cepheid-calibrated H0 (SH0ES hosts) | `CH0` |
| [candel-trgb](https://github.com/candel-cosmo/candel-trgb) | TRGB-calibrated H0 (EDD) | `EDD_TRGB` |
| [candel-mwcepheids](https://github.com/candel-cosmo/candel-mwcepheids) | Milky Way Cepheids | `MWCepheids` |
| [candel-maser](https://github.com/candel-cosmo/candel-maser) | Megamaser disk distances and H0 | own runners |

See the [CANDEL README](https://github.com/candel-cosmo/CANDEL#installation)
for installation.

- Documentation: [candel.readthedocs.io](https://candel.readthedocs.io)
- Contact: Richard Stiskalek (University of Oxford)
