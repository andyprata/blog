---
layout: post
title:  "How to install pyhdf with Macports"
date:   2018-04-03 15:53
categories: how to
---

First install HDF4

`$ sudo port install hdf4`

Make sure HDF4 external libraries are installed

`$ sudo port install jpeg`
`$ sudo port install zlib`
`$ sudo port install szip`

Now download the latest pyhdf tarball for UNIX from here, go to where ever you downloaded it and then unpack it with

`$ tar -xzvf pyhdf-0.9.0.tar.gz`

Note that this command does a couple things (copied from this post):
`f` : this must be the last flag of the command, and the tar file must be immediately after. It tells tar the name and path of the compressed file.
`z` : tells tar to decompress the archive using gzip.
`x` : tar can collect files or extract them. x does the latter.
`v` : makes tar talk a lot.

Now go into the new directory

`$ cd pyhdf-0.9.0`

Now here’s the crucial part. Since HDF4 was installed with macports we need to tell pyhdf where the HDF4 include and library files are

```python
export LIBRARY_DIRS=/opt/local/lib
export INCLUDE_DIRS=/opt/local/include
```

Finally we can install pyhdf using the following command

`$ sudo python setup.py install -i $INCLUDE_DIRS`
