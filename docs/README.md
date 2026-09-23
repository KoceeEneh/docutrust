# DocuTrust DevSecOps track: documentation

One walkthrough per chain. Each guide is a step-by-step build that a reader can
replicate against their own fork of this repository.

| Chain | Projects | Guide | Status |
|---|---|---|---|
| A: Detect | 1. SAST and secrets · 2. SCA and supply chain · 3. DAST, IAST, RASP | `chain-a-detect/` | not yet added |
| B: Prove | 4. SLSA provenance · 5. Sigstore signing and SBOM · 6. Admission control and graph correlation | [`chain-b-prove/`](chain-b-prove/) | added |
| C: Validate and Mature | 7. Continuous fuzzing · 8. · 9. | `chain-c-validate/` | not yet added |

## Layout for a new chain

```
docs/
  <chain-folder>/
    README.md                            what the chain covers and how to use the files
    DevSecOps-Chain-<X>-Guide.pdf        the guide
    DevSecOps-Chain-<X>-Guide.md         same content, for copying commands
    assets/screenshots/                  shot01.png, shot02.png, ...
    reference/                           finished config files, for reference only
```

## Conventions

- Folders and file names are lowercase kebab-case. Guide file names are the exception, to match how they are distributed.
- Chain folders are named `chain-<letter>-<chain-name>`.
- Screenshots are numbered in the order they appear in the guide.
- **Files under `reference/` are never live.** Workflows there are not in `.github/workflows/`, and manifests there are not applied by anything in this repository. Each project's own work is to build these, so a working copy in the active paths would pre-solve later projects (see the note at the end of `.github/workflows/ci.yml`).
- Guides don't change application code. The seeded findings in `src/` belong to the projects that target them, as the root `README.md` explains.
- Add one row to the table above when you add a chain.
