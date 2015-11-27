----------
CUBIEBOARD
==========
----------

Background
----------

Cubieboard is an open source project, initiated by Sylvain LEROY.
This project goal is to generate generic Debian images destinated to
Cubieboards plate-forms. The created image contains only a simple Debian
installation and it's up to you to specialize it if needed. Most of the
work is based on this page :
[Linux-Sunxi](http://linux-sunxi.org/Building_on_Debian)

Procedure
---------

1. Init the submodules with :

~~~sh
$ make initsm && make updatesm
~~~

The process may take a while, depending on your Internet speed.

2. Configure the Makefile
Please open the *makefile.vars* file, and modify the variables
depending of your needs. Take special attention to this ones :
 * `CUBIEBOARD_NAME` (version of the targeted plate-form)
 * `DTB` and `DTS` (device tree corresponding)
 * `DEB_ARCH` (target architecture)

3. Configure the Kernel
You must create the *.config* for your kernel. You can :
 * Choose a premade configuration file in the directory *conf*
and copy it to *linux-stable/.conf*
 * Manually choose which module to load by executing :

~~~sh
$ make kernel_menuconfig
~~~

  * Take the default sunxi config, by executint :

~~~sh
$ make kernel_defconfig
~~~

4. Now, you just have to launch the building process :

~~~sh
$ make all
~~~

The rule will compile u-boot and the kernel, make a debootstrap
and finally place everything in an image.

5. flash the generated file, placed in the *images* directory.

Contributors
------------

Sylvain LEROY <br />
Philippe THIERRY <br />
Jean GUYOMARC'H <br />
Louis SYOËN <br />
Arthur d'Avray <br />
Jean-Marc LACROIX

License
-------

*See COPYING file.*
