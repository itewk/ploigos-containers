# tssc-containers
![license](https://img.shields.io/github/license/rhtconsulting/tssc-containers)

Container image definitions for the TSSC project

## tssc-base
[![tssc-base](https://img.shields.io/badge/quay.io-tssc--base-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-base)

Defines the base TSSC container image, from which all other TSSC images derive.

## tssc-base-java-8
[![tssc-base-java-8](https://img.shields.io/badge/quay.io-tssc--base--java--8-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-base)

Defines a Java 8 base container image, built on top of `tssc-base`, from which many TSSC tool images derive.

## tssc-ci-agent-jenkins
[![tssc-ci-agent-jenkins](https://img.shields.io/badge/quay.io-tssc--ci--agent--jenkins-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-ci-agent-jenkins)

Defines a jenkins agent as a sidecar for the `tssc-tool-*` containers. Built from `tssc-base-java-8`.

## tssc-tool-argocd
[![tssc-tool-argocd](https://img.shields.io/badge/quay.io-tssc--tool--argocd-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-argocd)

Defines an ArgoCD container image. Built from `tssc-base`.

## tssc-tool-buildah
[![tssc-tool-buildah](https://img.shields.io/badge/quay.io-tssc--tool--buildah-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-buildah)

> **_NOTE:_** This image is not automatically built by GitHub actions because it requires to be built on a subscribed RHEL 8 machine.

Defines a buildah container image. Built from `tssc-base`.

## tssc-tool-config-lint
[![tssc-tool-config-lint](https://img.shields.io/badge/quay.io-tssc--tool--config--lint-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-config-lint)

Defines a [config-lint](https://github.com/stelligent/config-lint) container image. Built from `tssc-base`.

## tssc-tool-maven
[![tssc-tool-maven](https://img.shields.io/badge/quay.io-tssc--tool--maven-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-maven)

Defines a maven container image. Built from `tssc-base-java-8`.

## tssc-tool-openscap
[![tssc-tool-openscap](https://img.shields.io/badge/quay.io-tssc--tool--openscap-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-openscap)

> **_NOTE:_** This image is not automatically built by GitHub actions because it requires to be built on a subscribed RHEL 8 machine.

Defines an OpenSCAP based image scanning container image. Built from tssc-base.

## tssc-tool-skopeo
[![tssc-tool-skopeo](https://img.shields.io/badge/quay.io-tssc--tool--skopeo-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-skopeo)

Defines a skopeo container image. Built from `tssc-base`.

## tssc-tool-sonar
[![tssc-tool-sonar](https://img.shields.io/badge/quay.io-tssc--tool--sonar-lightgrey?logo=open-containers-initiative)](https://quay.io/repository/tssc/tssc-tool-sonar)

Defines a sonar-scanner container image. Built from `tssc-base`.

# Building locally for testing

The following commands can be used for building these images locally

```
# Run these commands from the directory where this repository was cloned

podman build -t tssc-base tssc-base
podman build --build-arg FROM_IMAGE=tssc-base -t tssc-base-java-8 tssc-base-java-8
podman build --build-arg FROM_IMAGE=tssc-base-java-8 -t tssc-tool-maven tssc-tool-maven
podman build --build-arg FROM_IMAGE=tssc-base-java-8 -t tssc-ci-agent-jenkins tssc-ci-agent-jenkins
podman build --build-arg FROM_IMAGE=tssc-base -t tssc-tool-skopeo tssc-tool-skopeo
podman build --build-arg FROM_IMAGE=tssc-base -t tssc-tool-argocd tssc-tool-argocd
```
