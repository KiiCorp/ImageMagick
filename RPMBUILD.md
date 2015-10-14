# How to build RPMs

1. install build tools
 ```
 $ sudo yum groupinstall "Development tools"
 $ sudo yum install rpmdevtools
 ```
1. run ```rpmdev-setuptree``` then create a work directory
```
$ rpmdev-setuptree
```
1. clone git repository and copy SPEC file
```
$ cd rpmbuild/SOURCES
$ git clone https://github.com/KiiCorp/ImageMagick.git
$ cp ImageMagick/ImageMagick.spec.kii ../SPECS/ImageMagick.spec
```
1. rename and archive source files
```
$ mv ImageMagick ImageMagick-6.4.0
$ tar zcvf ImageMagick-6.4.0.tar.gz ImageMagick-6.4.0
```

1. modify ```~/.rpmmacros``` like this to skip check-rpaths
```shell
%_topdir      %(echo $HOME)/rpmbuild
# %_smp_mflags  -j3
# %__arch_install_post   /usr/lib/rpm/check-rpaths   /usr/lib/rpm/check-buildroot
```

1. build RPMs
```
$ cd ..
$ rpmbuild -v -bb --clean SPECS/ImageMagick.spec
```
1. You will get RPMs in ```RPMS/x86_64``` !



