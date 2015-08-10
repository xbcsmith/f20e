# f20e


Bootstraping conary

Disable update repos

sed -i 's/enabled=0/enabled=1/g' /etc/yum.repos.d/fedora-updates.repo


sudo yum install gcc make patch tar git python-lxml python-epdb rpm-libs rpm-python openssl-devel python-crypto m2crypto zlib-devel elfutils-libelf-devel python-devel python-kid

mkdir -p work/

cd work/

git clone 'https://github.com/sassoftware/conary.git'

cd conary/conary/pysqlite3/

curl --remote-name  http://sqlite.org/sqlite-autoconf-3071201.tar.gz

tar -zxvf sqlite-autoconf-3071201.tar.gz

cd sqlite-autoconf-3071201

CLASSPATH="" CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector" CXXFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector " CPPFLAGS="" LDFLAGS="-g -O1 " CC=gcc CXX=g++  ./configure --prefix=/usr --exec-prefix=/usr --bindir=/usr/bin --sbindir=/usr/sbin --sysconfdir=/etc --datadir=/usr/share --includedir=/usr/include --libdir=/usr/lib64 --libexecdir=/usr/libexec --localstatedir=/var --sharedstatedir=/usr/com --mandir=/usr/share/man --infodir=/usr/share/info   --disable-shared --enable-threadsafe

CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector" CXXFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector " CPPFLAGS="" CLASSPATH=""  LDFLAGS="-g -O1 " CC=gcc CXX=g++  make    CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector -fPIC"

cd ../../

CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector" CXXFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector " CPPFLAGS="" CLASSPATH=""  LDFLAGS="-g -O1 " CC=gcc CXX=g++ CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector -fPIC"  make    PYINCLUDE=/usr/include/python2.7 PYTHON=/usr/bin/python2.7 PYVER=2.7 prefix=/usr bindir=/usr/bin datadir=/usr/share libelf=-lelf
CFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector" CXXFLAGS="-O2 -g -D_FORTIFY_SOURCE=2 -fstack-protector " CPPFLAGS="" CLASSPATH=""  LDFLAGS="-g -O1 " CC=gcc CXX=g++  make install PYINCLUDE=/usr/include/python2.7 PYTHON=/usr/bin/python2.7 PYVER=2.7 prefix=/usr bindir=/usr/bin datadir=/usr/share libelf=-lelf

sudo conary q



