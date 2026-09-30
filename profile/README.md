# CANDEL

**CANDEL** is a GPU-accelerated hierarchical Bayesian framework for the local
distance ladder and peculiar velocities, built on JAX and NumPyro. It
forward-models distance indicators from geometric megamaser anchors through
Cepheids and TRGB to peculiar-velocity tracers, and infers $H_0$, $S_8$ and
velocity-field parameters directly from the data.

## Getting started

Clone the core and the probes you need side by side in one folder, which also
holds the shared data and results:

```
candel-cosmo/
  CANDEL/  candel-pv/  candel-ch0/  ...   git checkouts
  data/  results/                         shared by every probe
```

Full steps, including the Python environment and `local_config.toml`, are in
the **[installation instructions](https://github.com/candel-cosmo/CANDEL#installation)**
([also on Read the Docs](https://candel.readthedocs.io)).

## How the repositories work

CANDEL is a core library plus one repository per probe.

- **[CANDEL](https://github.com/candel-cosmo/CANDEL)** is the core: inference
  (NUTS, evidence), selection integrals, field reconstructions, cosmography,
  run scripts and job submission, the documentation, and `local_config.toml`.
- **Probe packages** import the core; the core never imports them. Each one
  registers a `candel.Probe` under the `candel.probes` entry point, and the
  core's `main.py` picks it up from the config's `model.which_run` once the
  package is installed.
- Clone the probes you need **next to** `CANDEL`. Data and results sit in the
  same folder, outside every checkout, and all repositories find them through
  `root_data` and `root_results` in `CANDEL/local_config.toml`.

| Repository | Probe | `model.which_run` |
|---|---|---|
| [candel-pv](https://github.com/candel-cosmo/candel-pv) | Peculiar-velocity catalogues (TFR, FP, SNe), growth rate, S8 | `PV` (or unset) |
| [candel-ch0](https://github.com/candel-cosmo/candel-ch0) | Cepheid-calibrated H0 (SH0ES hosts) | `CH0` |
| [candel-trgb](https://github.com/candel-cosmo/candel-trgb) | TRGB-calibrated H0 (EDD) | `EDD_TRGB` |
| [candel-mwcepheids](https://github.com/candel-cosmo/candel-mwcepheids) | Milky Way Cepheids | `MWCepheids` |
| [candel-maser](https://github.com/candel-cosmo/candel-maser) | Megamaser disk distances and H0 | own runners |

## Papers using CANDEL

- Stiskalek et al. (2025), *The Velocity Field Olympics* — [arXiv:2502.00121](https://arxiv.org/abs/2502.00121)
- Stiskalek et al. (2025), *A 1.8 per cent measurement of $H_0$ from Cepheids alone* — [arXiv:2509.09665](https://arxiv.org/abs/2509.09665)
- Stiskalek et al. (2025), *No evidence for $H_0$ anisotropy from Tully--Fisher or supernova distances* — [arXiv:2509.14997](https://arxiv.org/abs/2509.14997)
- Stiskalek (2025), *$S_8$ from Tully--Fisher, Fundamental Plane and supernova distances* — [arXiv:2509.20235](https://arxiv.org/abs/2509.20235)
- Stiskalek et al. (2026), *Forward-modelling Milky Way Cepheids* — [arXiv:2603.09880](https://arxiv.org/abs/2603.09880)
- Stiskalek & Desmond (2026), *A reanalysis of the megamaser Hubble constant* — [arXiv:2609.17684](https://arxiv.org/abs/2609.17684)
- Stiskalek et al. (2026), *$H_0$ from the Tip of the Red Giant Branch and geometric anchors alone* — [arXiv:2609.29996](https://arxiv.org/abs/2609.29996)

- Documentation: [candel.readthedocs.io](https://candel.readthedocs.io)
- Contact: Richard Stiskalek (University of Oxford)
