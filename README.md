# All infos about [Benito Greybeard](https://github.com/settings/apps/benito-greybeard)

![](logo.png)

## Setup benito greybeard 

```shell
export HCLOUD_TOKEN=
ansible-navigator run ./setup-benito.yaml
```

## Build multi-arch ansible ee

```shell
podman login registry.redhat.io

export VERSION=$(date +%Y%m%d%H%M)
export IMAGE=quay.io/rbohne/benito-greybeard-ee:${VERSION}

ansible-builder create \
  --verbosity 3

podman build \
  --platform linux/amd64,linux/arm64 \
  --manifest ${IMAGE} context/    

podman manifest ${IMAGE}
```

For development it's easier to run:
```shell
ansible-builder build \
  --verbosity 3 \
  --container-runtime podman \
  --tag ${IMAGE}
```

