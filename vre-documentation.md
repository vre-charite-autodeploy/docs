# vre documentation

## self-hosting helm charts and images

If you want to fork the vre project and host the helm charts and container images used for the deployment of the vre
yourself, please note that several manual adjustments to the deployment code in the
[vre-infra repository](https://github.com/vre-charite-autodeploy/vre-infra).

If you fork to another GitHub organization, simply search and replace all occurrences of `vre-charite-autodeploy` as
well as `vre-charite` and replace them with the name of the organization you host your own helm charts and container
images.
If you changed names and/or versions, please make sure to adjust them accordingly as well.

If you forked away from GitHub, search and replace all occurrences of `ghcr.io/vre-charite-autodeploy` as well as
`ghcr.io/vre-charite` with the uris of your own helm and image registry, respectively.

Either way, if your own registries are private, ensure the host that runs the deployment has the correct credentials
available to access the helm registry.
Similarly, within the kubernetes cluster, the correct image pull secrets must be configured to successfully fetch
images from your private container registry.
