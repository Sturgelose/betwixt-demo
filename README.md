# Betwixt demo

This repository is a demo of [Betwixt](https://github.com/Sturgelose/betwixt). It holds the fleet files and the applications of the lab: one Raspberry Pi with Talos and Argo CD, with a lab stage and a staging stage.

A new version of an application goes to lab first. After it is healthy in lab for 15 minutes, it goes to staging.

| Folder | What it holds |
|---|---|
| `fleet/fleet.yaml` | The parts of the fleet that are the same for all profiles: the attribute schema, the project, the trust rule, and the pipeline. |
| `fleet/lab.yaml` | The profile `lab` and its cluster, the Raspberry Pi. |
| `fleet/staging.yaml` | The profile `staging` and its cluster `pi-staging`. The cluster shares the Raspberry Pi with `pi` and uses the prefix `stg`. The old cluster `staging-demo` is decommissioned. |
| `apps/` | One folder for each application. Each folder has a `betwixt.yaml` and its values. |

The workflow `lab` applies the fleet files and pushes each application from `main`. It authenticates with the OIDC token of GitHub Actions, so it needs no secret.

To add an application, add a folder under `apps/` with its `betwixt.yaml`.
