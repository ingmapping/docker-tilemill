# docker-tilemill
 
This repository contains instructions for building a Docker image thats runs a container with Tilemill.

Tilemill allows you to:

* Use existing projects as a starting point 
* Define styling rules with CartoCSS which define layer colours and visibility
* Export maps in image format or as a package of raster tiles in mbtiles format

More information: https://wiki.openstreetmap.org/wiki/TileMill and https://github.com/tilemill-project/tilemill.

# docker-tilemill set up

How to build the image:

```
docker build -t ingmapping/tilemill git://github.com/ingmapping/docker-tilemill
```

or 

```
docker pull ingmapping/tilemill
```

To run you must expose 20008 and 20009 port using -p 20008:20008 -p 20009:20009. How to run the container:

```
docker run --name="docker-tilemill" -p 20008:20008 -p 20009:20009 -d -t ingmapping/tilemill
```
To use your local projects you cant mount your project direcotry using -v argument. How to mount your local ~/Documents/Mapbox in the container in order to work on data from your local filesystem: 

```
docker run -d --name="docker-tilemill" -p 20008:20008 -p 20009:20009 -v ~/Documents/MapBox/project/:/root/Documents/MapBox/project/ -t ingmapping/tilemill
```

To use the container, open your browser at:

```
http://localhost:20009
```



