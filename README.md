[Skopeo](https://github.com/containers/skopeo) allows for sync container images between different repositories.
This git repository contains a patch file which add parameter to prepend the destination image name's with prefix.

The GitLab container repository are published in path "username/project/container" and we cannot sync these images for example to Docker Hub, which supports only path "username/container".
The patch file add additional parameter to command skopeo sync ("prepend-image-suffix"), which allow us to sync images from GitLab to DockerHub. The original container image name will be prepend with prefix defined durning execution of skope sync.

For example containers stored in path "username/project/container" will be published under name username/project-container" if you call skopeo sync --prepend-image-suffix project- --src docker --dest docker registry.gitlab.com/<your-username>/<your-project>/<your-container> docker.io/<your-docker-hub-username>

At the moment in skopeo repository are a few similar issues/PR:
* [WIP added implementation for scoped-without-registry support on sync #1100](https://github.com/containers/skopeo/pull/1100)
* [feat: add a per-repo destination-path-style setting for yaml source #1769 ](https://github.com/containers/skopeo/pull/1769)
