# tileoven-centos7-dependencies
Dependencies to build and install Tileoven on Centos 7.5.

Before building [Tileoven](https://github.com/andydekiert/tileoven) on Centos 7.5 you will need to build and install these dependencies. This repository will allow you to conveniently download versions of Mapnik and NodeJS which have been used to successfully build Tileoven on CentOS. Suggestion is to clone this repository to your `~/Downloads` folder, follow the instructions below and finally delete the repo from your drive again, as it will no longer be needed.

## Build and install Mapnik 2.2.0
1. Start by installing the build dependencies of Mapnik 2.2.0:
   ```
   yum install postgresql-devel sqlite-devel
   yum install cairo-devel pycairo-devel
   yum install gdal-devel
   yum install boost-devel boost
   yum install proj-devel proj-epsg
   yum install libtiff-devel libpng-devel libjpeg-devel
   yum install libicu-devel
   yum install libxml2-devel xml2
   yum install freetype-devel
   ```

2. Next: Extract `mapnik-v2.2.0.tar.bz2` to a location of your liking, e.g. `/usr/local/src`.

3. Build and install Mapnik. Open a terminal and navigate to where you just extracted the tarball. Then execute with root privileges:
   ```bash
   ./configure
   make
   make install
   ```
   
4. Test Mapnik
   ```bash
   make test
   ```
   It's likely that there will be some so called errors.
   Reason: Mapnik test renders some predefines tiles and compares them pixel-by-pixel to reference tiles. Usually there are a few pixels different but still indistinguishable for a human. Just check the output and follow the instructions to check the HTML test report which will be generated.


## Build and install NodeJS 6.9.1
1. Extract `node-v6.9.1.tar.gz` to a location of your liking, e.g. `/usr/local/src`.

2. Build and install NodeJS. Open a terminal and navigate to where you just extracted the tarball. Then execute with root privileges:
   ```bash
   ./configure
   make
   make install
   ```
   
3. Check installed NodeJS version
   ```bash
   node --version
   ```


