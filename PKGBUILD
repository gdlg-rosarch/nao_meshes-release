# Script generated with Bloom
pkgdesc="ROS - meshes for the Aldebaran Robotics NAO"
url='http://github.com/vrabaud/nao_meshes/'

pkgname='ros-kinetic-nao-meshes'
pkgver='0.1.11_2'
pkgrel=1
arch=('any')
license=('Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License'
)

makedepends=('jdk7-openjdk'
'ros-kinetic-catkin'
)

depends=()

conflicts=()
replaces=()

_dir=nao_meshes
source=()
md5sums=()

prepare() {
    cp -R $startdir/nao_meshes $srcdir/nao_meshes
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

