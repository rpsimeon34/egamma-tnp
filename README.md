# egamma-tnp

[![ci](https://github.com/ikrommyd/egamma-tnp/actions/workflows/ci.yml/badge.svg)](https://github.com/ikrommyd/egamma-tnp/actions?query=workflow%3ACI%2FCD+event%3Aschedule+branch%3Amaster)
[![PyPI Version](https://badge.fury.io/py/egamma-tnp.svg)](https://badge.fury.io/py/egamma-tnp)
![Downloads](https://img.shields.io/pypi/dm/egamma-tnp.svg)

E/Gamma Tag & Probe framework using [coffea](https://github.com/CoffeaTeam/coffea).

Forked from ikrommyd. To be eventually extended to a muon tnp framework.

## Next Steps

This is a roadmap for some next steps. At each step, reach out to the group members to discuss the progress. Also, please ask questions in the Slack, over email, and in meetings!

1. Clone this fork of the repo
  a. `git clone git@github.com:rpsimeon34/egamma-tnp.git`
2. Install the package (`-e` for editable install)
  b. `cd egamma-tnp && python3 -m pip install -e .`
3. Run the tests in the `tests` directory
  a. `cd tests && python3 test_cli.py`
4. In a notebook or script, instantiate an `ElectronTagNProbeFromNanoAOD` object and use `get_1d_pt_eta_phi_tnp_histograms` to obtain histograms
  a. Use the fileset used in `test_cli.py` and the default filters/triggers/values from `test_cli.py`
  b. Plot the resulting histograms (pt, eta, phi) for passing probes, failing probes, and all probes
  c. Plot the ratio of pt(and eta and phi) histograms for (passing probes)/(all probes) - this is a preliminary efficiency
  d. Set `cut_and_count` to False to also get invariant mass histograms
  e. Get an invariant mass plot for each of (tag+passing probe), (tag+failing probe), and (tag+any probe)
5. Make a DYtoLL fileset
  a. Use 2024 MC (you can use the `fileset_maker.ipynb` also used for `zxxhbb`, for example)
6. Re-do 4, but with the DYtoLL fileset and the di-lepton trigger we want to study
  a. Use `test_cli.py` as an example
  b. Leave any keywords in the `ElectronTagNProbeFromNanoAOD` initialization to default, if you aren't sure what they do
  c. Use a tag pt threshold slightly tighter than the trigger's strictest pt requirement
  d. Use a probe pt threshold moderately looser than the trigger's looser pt requirement
  e. Record all the keywords you use when initializing `ElectronTagNProbeFromNanoAOD`. Write in a slide what those keywords mean, or write that you don't know what it does, so we can look into it together.
  f. The deliverable here is a set of slides with the info from 6e, the samples used in 5a, the total number of events in each sample in 5a **that we ran over when making the plots**, and the plots from (4b, 4c, and 4e but redone for step 6)
7. Make a data fileset
  a. Use 2024 EGamma 0 and 1
8. Re-do 6, but with the data fileset from 7
  a. We want the deliverable from 6f again, but redone for data

After this, we will have to implement a fitting strategy to extract an efficiency from the invariant mass plots. We will also start looking into extending to muons, but let's accomplish these steps first before moving to muons.
