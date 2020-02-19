
# Maintainer: 
pkgname="ros-melodic-franka-msg"
pkgver="0.6.0"
pkgrel=1
pkgdesc="franka_msgs provides messages specific to Franka Emika research robots"
arch=('x86_64')
url="http://wiki.ros.org/franka_msgs"
license=('Apache 2.0')

makedepends=(

'ros-melodic-message-generation'

)

depends=(

'ros-melodic-message-runtime'

)

provides=($pkgname)
conflicts=($pkgname)
_dir="franka_ros-release-release-melodic-franka_msgs-0.6.0-1"
source=("$pkgname-$pkgver.tar.gz::https://github.com/frankaemika/franka_ros-release/archive/release/melodic/franka_msgs/0.6.0-1.tar.gz")
md5sums=('157f5d83dc0d3403809f0d70ffd6214f')

build() {
	# Use ROS environment variables
  	source /usr/share/ros-build-tools/clear-ros-env.sh
  	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create build directory
  	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  	cd ${srcdir}/build

	# Build project
	cmake ${srcdir}/${_dir} \
	      -DCMAKE_BUILD_TYPE=Release \
	      -DCATKIN_BUILD_BINARY_PACKAGE=ON \
	      -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
	      -DPYTHON_EXECUTABLE=/usr/bin/python3 \
	      -DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
