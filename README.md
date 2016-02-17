# jmfirth/docker-webpack

> Webpack-based development and build toolchain in a container

[Develop](#example:-watch-and-serve) and [build](#example:-build) JavaScript applications using [webpack][webpack--url] and [webpack-dev-server][webpack-dev-server--url] with ease!  Get all the bells and whistles of modern [Node.js][nodejs--url] and/or web application development without the hassle of installing an environment.


## Available Images

This image uses the [official Node.js image][docker_hub_node--url] on the [Docker Hub][docker_hub--url] as it's base, following their tag convention.  Below is a list of currently available tags:

| Tags | Environment |
|------|-------------|
| [latest][dockerfile-latest] | Node.js latest on Debian Wheezy |
| [5.6][dockerfile-5.6] | Node.js 5.6 on Debian Jessie |
| [4.3][dockerfile-4.3] | Node.js 4.3 on Debian Jessie |
| [wheezy][dockerfile-wheezy] | Node.js latest on Debian Wheezy |
| [slim][dockerfile-slim] | Node.js latest on Debian Jessie |
| [5.6-wheezy][dockerfile-5.6-wheezy] | Node.js 5.6 on Debian Wheezy |
| [5.6-slim][dockerfile-5.6-slim] | Node.js 5.6 on Debian Jessie |
| [4.3-wheezy][dockerfile-4.3-wheezy] | Node.js 4.3 on Debian Wheezy |
| [4.3-slim][dockerfile-4.3-slim] | Node.js 4.3 on Debian Jessie |


## Installing the Image

Install latest:

```sh
$ docker pull jmfirth/webpack
```

## Running the Image

The image preinstalls webpack and webpack-dev-server for use in the interactive docker shell.  Any valid webpack and webpack-dev-server command can be run.

### Example: Install Npm Dependencies

An example of installing project npm dependencies.

_Note: Assumes that `project.json` exists at source root._

```sh
$ docker run \
  --rm \
  -i \
  -t \
  -v /path/to/source:/app \
  jmfirth/webpack \
  npm install --no-bin-links
```

### Example: Watch and Serve

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

### Example: Build

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


### Full Example

Create a docker machine:

```sh
# create a docker machine called "site"
$ docker-machine create site --driver=virtualbox

# get environment variables to new vm
$ eval "$(docker-machine env site)"
```

Obtain and prepare source:

```sh
# get some source that uses webpack
$ git clone https://github.com/petehunt/react-webpack-template.git src
$ cd src

# install npm dependencies
$ docker run \
  --rm \
  -i \
  -t \
  -v /path/to/src:/app \
  jmfirth/webpack \
  npm install --no-bin-links
```

Modify the `webpack.config.js` file to watch by polling:

```
watchOptions: {
   poll: true
}
```

Serve the app:

```sh
# serve app through webpack-dev-server
$ docker run \
  --rm \
  -i \
  -t \
  -v /path/to/src:/app \
  -p 3000:8080 \
  jmfirth/webpack \
  webpack-dev-server --hot --inline --progress --host 0.0.0.0
```

[nodejs--url]: https://github.com/nodejs/node
[webpack--url]: https://github.com/webpack/webpack
[webpack-dev-server--url]: https://github.com/webpack/webpack-dev-server
[docker_hub--url]: hub.docker.com
[docker_hub_node--url]: https://hub.docker.com/_/node/
[dockerfile-latest]: https://github.com/jmfirth/docker-webpack/blob/master/latest/Dockerfile
[dockerfile-5.6]: https://github.com/jmfirth/docker-webpack/blob/master/5.6/Dockerfile
[dockerfile-4.3]: https://github.com/jmfirth/docker-webpack/blob/master/4.3/Dockerfile
[dockerfile-wheezy]: https://github.com/jmfirth/docker-webpack/blob/master/wheezy/Dockerfile
[dockerfile-slim]: https://github.com/jmfirth/docker-webpack/blob/master/slim/Dockerfile
[dockerfile-5.6-wheezy]: https://github.com/jmfirth/docker-webpack/blob/master/5.6/wheezy/Dockerfile
[dockerfile-5.6-slim]: https://github.com/jmfirth/docker-webpack/blob/master/5.6/slim/Dockerfile
[dockerfile-4.3-wheezy]: https://github.com/jmfirth/docker-webpack/blob/master/4.3/wheezy/Dockerfile
[dockerfile-4.3-slim]: https://github.com/jmfirth/docker-webpack/blob/master/4.3/slim/Dockerfile
