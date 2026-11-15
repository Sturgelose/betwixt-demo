# Betwixt demo

This repository is a demo of [Betwixt](https://github.com/Sturgelose/betwixt). It holds the fleet files and the applications of the lab: one Raspberry Pi with Talos and Argo CD.

| Folder | What it holds |
|---|---|
| `fleet/` | The fleet files: the attribute schema, the profile, the project, the trust rule, the cluster, and the pipeline. |
| `apps/` | One folder for each application. Each folder has a `betwixt.yaml` and its values. |

The workflow `lab` applies the fleet files and pushes each application from `main`. It authenticates with the OIDC token of GitHub Actions, so it needs no secret.

To add an application, add a folder under `apps/` with its `betwixt.yaml`.
