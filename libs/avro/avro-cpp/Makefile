#
# avro - Makefile for Apache Avro library
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=avro-cpp
PKG_VERSION:=1.8.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://archive.apache.org/dist/avro/avro-$(PKG_VERSION)/cpp
PKG_HASH:=5328b913882ee5339112fa0178756789f164c9c5162e1c83437a20ee162a3aab

PKG_MAINTAINER:=Jiri Kastner <cz172638@gmail.com>

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/avro-cpp
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+jansson +boost +boost-system +boost-filesystem +boost-iostreams \
	  +boost-program_options +boost-regex +zlib +bzip2
  TITLE:=Apache Avro C++ Library
  URL:=https://avro.apache.org
endef

define Package/avro-cpp/description
  This package contains the Apache Avro C++ library.
endef

CMAKE_OPTIONS += \
        -DCMAKE_BUILD_TYPE:STRING=MINSIZEREL

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libavrocpp.so* $(1)/usr/lib/
endef

define Package/avro-cpp/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libavrocpp.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,avro-cpp))

