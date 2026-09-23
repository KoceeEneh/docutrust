# Chain B: Prove (Projects 4, 5 and 6)

A step-by-step build a reader can replicate against their own fork of DocuTrust.
It answers one question about the container image: can we prove where it came
from, that it hasn't been changed, and stop anything we can't prove from running?

| Project | What it builds | Tools |
|---|---|---|
| 4. SLSA provenance | CI builds and publishes the image to GHCR with signed SLSA provenance, then tests it: OIDC token forgery attempt, ephemeral runner proof, two verifiers | GitHub Actions, `attest-build-provenance`, `gh attestation verify`, slsa-verifier |
| 5. Sigstore signing and SBOM | Keyless signature and a signed SPDX SBOM, both from CI, then a tampering test and an identity-forgery test | Cosign, Fulcio, Rekor, Syft |
| 6. Admission control and correlation | Kyverno admits only images signed by the pipeline and carrying a pipeline-signed SBOM; GUAC answers whether the shipped image contains a known vulnerable package | k3d, Kyverno, GUAC, OSV |

## Files

| File | What it is |
|---|---|
| `DevSecOps-Chain-B-Guide.pdf` | The guide, for reading |
| `DevSecOps-Chain-B-Guide.md` | The same content, for copying commands (PDF viewers break long lines) |
| `assets/screenshots/` | Figures used in the guide |
| `reference/provenance.yml` | The finished workflow |
| `reference/k8s/` | The finished Kyverno policies and admission test pods |

## About `reference/`

**These files are not live.** The workflow is not in `.github/workflows/` and the
manifests are not applied by anything in this repository, so Projects 4–6 are
not pre-solved for anyone working through them (see the note at the end of
`.github/workflows/ci.yml`). Placeholders like `<owner>` must be replaced before
use.

## Starting point

The guide starts from this repository as it ships, with the Project 1–3 code
fixes not applied. The seeded weaknesses, including `lodash@4.17.15`, are still
present, and Project 6 uses the unpatched lodash as its test case.

Written, built and tested by Kosisochukwu Eneh.
