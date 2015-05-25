## 64-bit adjustments for Glassfish pkg

Adjusted source-code to enable the use of bundled "pkg" tool of Glassfish 4 in 64 bit OS. The main guidelines are taken from [this blog post] (https://blog.kumina.nl/2010/07/glassfish-3-0-1s-pkg-tool-using-debians-python-packages/) and updates from [this forum thread] (https://www.java.net/forum/topic/glassfish/glassfish/how-make-pkg-work-glassfish-4-kubuntu-1404-x64). Steps to run the "pkg" under 64 bit OS-es:

1. `apt-get install python-dev gcc python-cherrypy python-mako python-openssl python-ply python-pycurl python-simplejson `
1. Download `_actions.c` from this project (you can clone the project if you have git installed on the server)
1. `gcc -I/usr/include/python2.7 -shared -fpic -O2 _actions.c -o _actions.so`
1. Hit the "pkg" tool: `/opt/glassfish/bin/pkg`
1. `mv /opt/glassfish/pkg/bin/pkg /opt/glassfish/pkg/bin/pkg.orig`
1. Download `pkg` from this project and copy to /opt/glassfish/pkg/bin/pkg
1. `mkdir /opt/glassfish/pkg/custom-lib`
1. `cp -r /opt/glassfish/pkg/vendor-packages/pkg /opt/glassfish/pkg/custom-lib`
1. `cp _actions.so /opt/glassfish/pkg/custom-lib/pkg/actions/_actions.so`
1. download __init__.py from this folder
1. `cp __init__.py /opt/glassfish/pkg/custom-lib/pkg/actions/__init__.py`
1. enjoy
