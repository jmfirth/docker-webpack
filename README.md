# jmfirth/docker-webpack

> Webpack-based development and build toolchain in a container

[Develop](###watch-and-serve) and [build](###build) JavaScript applications using [webpack][webpack--url] and [webpack-dev-server][webpack-dev-server--url] with ease!  Get all the bells and whistles of modern [Node.js][nodejs--url] and/or web application development without the hassle of installing an environment.


## Available Images

This images uses the [official Node.js image][docker_hub_node--url] on the [Docker Hub][docker_hub--url] as it's base, following their tag convention.  Below is a list of currently available tags:

| Tags | Environment |
|------|-------------|
| latest | Node.js 5.6 on Debian Wheezy |
| wheezy | Node.js 5.6 on Debian Wheezy |
| slim | Node.js 5.6 on Debian Jessie |
| wheezy-5.6 | Node.js 5.6 on Debian Wheezy |
| wheezy-4.3 | Node.js 4.3 on Debian Wheezy |
| slim-5.6 | Node.js 5.6 on Debian Jessie |
| slim-4.3 | Node.js 4.3 on Debian Jessie |


## Install Image

Install latest:

```sh
$ docker pull jmfirth/webpack
```

## Running Image

The image preinstalls webpack and webpack-dev-server for use in the interactive docker shell.  Any valid webpack and webpack-dev-server command can be run.

### Watch and Serve

An example of watching and serving the app using webpack-dev-server.

_Note: Assumes that default `webpack.config.js` exists at source root._

```sh
$ docker run \
  --rm \
  -i \
  -t \
  -v /path/to/source:/app \
  -p 3000:8080 \
  jmfirth/webpack \
  webpack-dev-server --hot --inline --progress --host 0.0.0.0
```

### Build

An example of building the app with webpack.

_Note: Assumes that default `webpack.config.js` exists at source root._

```sh
$ docker run \
  --rm \
  -i \
  -t \
  -v /path/to/source:/app \
  jmfirth/webpack \
  webpack
```

[nodejs--url]: https://github.com/nodejs/node
[webpack--url]: https://github.com/webpack/webpack
[webpack-dev-server--url]: https://github.com/webpack/webpack-dev-server
[docker_hub--url]: hub.docker.com
[docker_hub_node--url]: https://hub.docker.com/_/node/
