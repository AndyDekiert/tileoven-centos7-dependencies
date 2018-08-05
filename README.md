# tileoven-centos7-dependencies
Dependencies to build and install TileOven on Centos 7.5.

Before building [TileOven](https://github.com/andydekiert/tileoven) on Centos 7.5 you will need to build and install these dependencies. This repository will allow you to conveniently download versions of Mapnik and NodeJS which have been used to successfully build Tileoven on CentOS. Suggestion is to clone this repository to your `~/Downloads` directory, follow the instructions below and finally delete the repo from your drive again, as it will no longer be needed.

To clone to your `~/Downloads` directory:
```
cd ~/Downloads
git clone https://github.com/andydekiert/tileoven-centos7-dependencies
```

## Build and install Mapnik 3.0.20
1. Start by installing the build dependencies of Mapnik 3.0.20:
   ```
   yum install postgresql-devel sqlite-devel
   yum install cairo-devel pycairo-devel
   yum install gdal-devel
   yum install boost-devel boost
   yum install proj-devel proj-epsg
   yum install libtiff-devel libpng-devel libjpeg-devel
   yum install libicu-devel
   yum install libxml2-devel xml2
   yum install libwebp-devel
   yum install freetype-devel
   ```
   Single command:
   ```bash
   yum install postgresql-devel sqlite-devel cairo-devel pycairo-devel gdal-devel boost-devel boost proj-devel proj-epsg libtiff-devel libpng-devel libjpeg-devel libicu-devel libxml2-devel xml2 libwebp-devel freetype-devel
   ```
   
2. Install a more up-to-date compiler using the SCL feature of CentOS:
   ```bash
   yum install centos-release-scl
   yum install devtoolset-7
   scl enable devtoolset-7 bash
   gcc --version
   ```
   GCC version should be > 7.3.1 now. Although Mapnik and later node-mapnik only need gcc > 5. 

3. Next: Extract `mapnik-v3.0.20-modified.tar.bz2` to a location of your liking, e.g. `/usr/local/src`.

   On my system I had to edit the make file for a successfull build. Following the instructions from a similiar [issue](https://github.com/mapnik/mapnik/issues/3384) I edited the `makefile`. The tarball already contains that change - hence the "modified".

5. Build and install Mapnik. Open a terminal and navigate to where you just extracted the tarball. Then execute with root privileges:
   ```bash
   ./configure --with-libraries=all
   make
   make install
   ```
   
6. Test Mapnik
   ```bash
   make test
   ```
   It's likely that there will be some so called errors.
   Reason: Mapnik test renders some predefined tiles and compares them pixel-by-pixel to reference tiles. Usually there are a few pixels different but for a human the entire image is still indistinguishable from the reference. Just check the output and follow the instructions to review the HTML test report which will be generated.


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


