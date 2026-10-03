#
# Copyright (C) 2007-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=argp-standalone
PKG_VERSION:=1.5.0

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/argp-standalone/argp-standalone.git
PKG_SOURCE_VERSION:=8ded2bc942740b5d291e450af661c5090dc3ca38
PKG_MIRROR_HASH:=6614c311f458fbeeba6e36651bc5d6426661461aa694e1a8e07eefc2d52e22f0
PKG_MAINTAINER:=Ted Hess <thess@kitschensync.net>

PKG_LICENSE:=LGPL-2.1
PKG_LICENSE:=Makefile.am

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/meson.mk

define Package/argp-standalone
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Hierarchial argument parsing broken out from glibc
  URL:=http://www.lysator.liu.se/~nisse/misc/
endef

define Package/argp-standalone/description
  GNU libc hierarchial argument parsing library broken out from glibc.
endef

MAKE_FLAGS += \
	CFLAGS="$(TARGET_CFLAGS) $(FPIC)"

HOST_MAKE_FLAGS += \
	CFLAGS="$(HOST_CFLAGS) $(FPIC)"

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP)   $(PKG_BUILD_DIR)/argp.h \
		$(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP)   $(MESON_BUILD_DIR)/libargp.a \
		$(1)/usr/lib/
endef

define Host/Install
	$(INSTALL_DIR) $(1)/include
	$(CP)   $(HOST_BUILD_DIR)/argp.h \
		$(1)/include/
	$(INSTALL_DIR) $(1)/lib
	$(CP)   $(MESON_HOST_BUILD_DIR)/libargp.a \
		$(1)/lib/
endef

$(eval $(call BuildPackage,argp-standalone))
$(eval $(call HostBuild))
