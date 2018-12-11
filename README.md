# vCenter Appliance Simulator

A VMware [vCenter API mock server](https://github.com/vmware/govmomi/tree/master/vcsim") based on [govmomi](https://github.com/vmware/govmomi). This dockerized version provides save defaults for a quick setup. The readme aims to get you started quickly when you need a vCenter API to test your code on.

## Help

To display the supported `vcsim` options just run `docker run m451/vcsim -h`, which will override the default container `CMD`.

## Building

If you want to build your own Docker image using this source simply run the following commands:

``` bash
docker build . --build-arg https_proxy=https://http-proxy:8080
docker tag IMAGEID repo/name:version
docker tag IMAGEID repo/name:latest
```

Replace `IMAGEID` with the resulting image hash of the `build` operation. Replace `repo` with your repo name, `name` with the name for the image and `version` with an optional version string for the build. The special version name `latest` enables you to reference the image without specifing a version.

## Starting the mock server

To start the mock server on port 8989 *(default used by vcsim)* simply run the container and specify the container host port to map the container port on *(8989 in this example)*.

``` bash
docker run -p 8989:8989 m451/vcsim
```

You can then list the available API methods by opening the [about page](https://127.0.0.1:8989/about) in a browser or crawl them using tools like `curl`:

``` bash
curl -sk https://user:pass@127.0.0.1:8989/about
```
