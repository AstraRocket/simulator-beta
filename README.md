# AstraRocket (beta)

**▶ [Launch the beta](https://astrarocket.github.io/simulator-beta/)**

This repository publishes the **beta** build of [AstraRocket](https://github.com/AstraRocket/simulator), the browser-based UI for the OpenRocket engine. The beta site runs the `beta` branch of [AstraRocket/simulator](https://github.com/AstraRocket/simulator): a snapshot of the `dev` branch, held still while it is tested before it goes to the [production site](https://astrarocket.github.io/simulator/). It gets new features and fixes before production does.

There is no app source here. This repository exists because GitHub Pages gives each repository one site, so the beta needs a repository of its own to publish to.

## Using the beta

- **Expect rough edges.** The beta is a release candidate, not a release. Use the [production site](https://astrarocket.github.io/simulator/) for anything you rely on.
- **Your data is kept apart from the other sites.** The beta uses its own browser storage, so rockets, motors, materials and settings saved here do not show up on the production, dev or hotfix sites, and nothing you do in the beta touches your production designs. Move a design between them by exporting a `.ork` from one and importing it in the other.
- **It can be installed separately.** The installed app, its name and its version are labeled beta, so it can sit beside the production install.
- **Version numbers name the build.** A beta version reads like `1.2.3-beta.45`, where the last number is the deploy run. Include it when reporting a problem.

## Reporting problems

Open an issue on [AstraRocket/simulator](https://github.com/AstraRocket/simulator/issues), not here, and include the version shown in the app.

## How the site is deployed

The build itself lives in the main repository, in [`.github/workflows/channel-deploy.yml`](https://github.com/AstraRocket/simulator/blob/beta/.github/workflows/channel-deploy.yml) on the `beta` branch. This repository's [`.github/workflows/deploy-beta.yml`](.github/workflows/deploy-beta.yml) only calls it, with `channel: beta`.

To publish the beta:

1. Open **Actions → Deploy beta** in this repository.
2. Click **Run workflow**.

The called workflow checks out the `beta` branch of AstraRocket/simulator, builds the app and its docs with the `/simulator-beta/` base path and `APP_CHANNEL=beta`, and deploys the result to this repository's Pages site. Because a called workflow runs as its caller, the run, its Pages deployment and its token all belong to this repository; the main repository is only read. Nothing in the main repository can start this deploy, so it cannot publish over the production site.

### Setup

Pages for this repository must be set to deploy from **GitHub Actions** (Settings → Pages → Build and deployment → Source).
