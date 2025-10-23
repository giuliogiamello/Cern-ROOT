# Cern-ROOT

## ROOT - Installation tutorial

Today is `2025/10/08`

In order to install ROOT, you need all the dependencies, so go to:

- [Dependencies - ROOT](https://root.cern.ch/install/dependencies/)
- [Dependencies - ROOT: Ubuntu and other Debian-based distributions](https://root.cern.ch/install/dependencies/#ubuntu-and-other-debian-based-distributions)

and install:

```
sudo apt install binutils cmake dpkg-dev g++ gcc libssl-dev git libx11-dev \
libxext-dev libxft-dev libxpm-dev python3 libtbb-dev libvdt-dev libgif-dev
```

then the (optional) packages:

```
sudo apt install gfortran libpcre3-dev \
libglu1-mesa-dev libglew-dev libftgl-dev \
libfftw3-dev libcfitsio-dev libgraphviz-dev \
libavahi-compat-libdnssd-dev libldap2-dev \
 python3-dev python3-numpy libxml2-dev libkrb5-dev \
libgsl-dev qtwebengine5-dev nlohmann-json3-dev libmysqlclient-dev \
libgl2ps-dev \
liblzma-dev libxxhash-dev liblz4-dev libzstd-dev
```

- Download the source code [Building ROOT from source - ROOT](https://root.cern.ch/install/build_from_source/)

Create a main folder, I created `mkdir root_home`.
Move inside it and git clone the source code with:

```
$ git clone --branch latest-stable --depth=1 https://github.com/root-project/root.git root_src
```

- Inside `root_home` create a build and install directories, I named `root_build` and `root_install`, respectively.

Then move into `root_build` and execute the `cmake` command on the shell:

```
cmake -DCMAKE_INSTALL_PREFIX=~/root_home/root_install ~/root_home/root_src 
```

- Build the programme, you can specify the number `N` of threads with the option `-jN`. (You should be connected to internet to build it).

```
cmake --build . --target install -j4
```

Then move to `~/root_home/root_install/bin` and from here write the following in the `.bashrc` file, to source ROOT setup automatically at each login

```
echo ". ~/root_home/root_install/bin/thisroot.sh" >> ~/.bashrc
```

- Close your terminal and open a new one
- Test ROOT

```
root
```

should give you an output like this:

```
jamal@giulio-pc:~$ root
   ------------------------------------------------------------------
  | Welcome to ROOT 6.36.04                        https://root.cern |
  | (c) 1995-2025, The ROOT Team; conception: R. Brun, F. Rademakers |
  | Built for linuxx8664gcc on Oct 08 2025, 18:40:35                 |
  | From tags/6-36-04@6-36-04                                        |
  | With c++ (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0                   |
  | Try '.help'/'.?', '.demo', '.license', '.credits', '.quit'/'.q'  |
   ------------------------------------------------------------------

root [0] 
```

Done!
