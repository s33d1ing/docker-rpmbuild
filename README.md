# Docker RPM Build Environment

These images are based on the official [CentOS](https://hub.docker.com/_/centos) images and have been modified to package the [GNU Hello](https://www.gnu.org/software/hello/) project.

## Supported Architectures

Although the CentOS images support multiple architectures, these images are only built as `x86-64`.

## Usage

Here are some example snippets to help you get started creating a container.

### docker-compose

```yaml
version: "3.8"

services:
  centos-7:
    image: s33d1ing/rpmbuild:el7
    volumes:
      - ./artifacts/7:/home/worker/rpmbuild/RPMS

  centos-8:
    image: s33d1ing/rpmbuild:el8
    volumes:
      - ./artifacts/8:/home/worker/rpmbuild/RPMS
```

### docker cli

```shell
docker run -d --name=rpmbuild-el7 -v ./artifacts/7:/home/worker/rpmbuild/RPMS s33d1ing/rpmbuild:el7

docker run -d --name=rpmbuild-el8 -v ./artifacts/8:/home/worker/rpmbuild/RPMS s33d1ing/rpmbuild:el8
```

## Parameters

| Parameter | Function |
| --- | --- |
| `-v /home/worker/rpmbuild/RPMS` | Output directory. |

## Building locally

If you want to make local modifications to these images for development purposes or just to customize the logic:

```shell
git clone https://github.com/s33d1ing/docker-rpmbuild.git

cd docker-rpmbuild

docker-compose up -d --build
```
