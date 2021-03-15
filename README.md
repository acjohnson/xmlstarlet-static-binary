# xmlstarlet-static-binary

This binary was compiled using these steps

```shell
# git clone git://git.code.sf.net/p/xmlstar/code --branch 1.6.1 --depth 1 xmlstar-code
# cd xmlstar-code
# wget https://raw.githubusercontent.com/spritsail/plex-media-server/master/xmlstarlet-0001-Fix-disable-build-docs.patch
# git apply xmlstarlet*.patch

# export CFLAGS=-static
# export CPPFLAGS=-static
# export LDFLAGS=-static

# autoreconf -sif

## I had to download and compile libxml2 and libxslt to statically link xmlstarlet...
## Also I had to do some wacky symlinking in $HOME/libxslt/libexslt/.libs ...

./configure \
        --prefix=/usr \
        --disable-build-docs \
        --with-libxml-prefix=/usr \
        --with-libxml-include-prefix=$HOME/libxml2/include \
        --with-libxml-libs-prefix=$HOME/libxml2/.libs \
        --with-libxslt-prefix=/usr \
        --with-libxslt-include-prefix=$HOME/libxslt \
        --with-libxslt-libs-prefix=$HOME/libxslt/libexslt/.libs \
        --enable-static-libs
```

For license info and source code visit http://xmlstar.sourceforge.net/
