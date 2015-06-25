
# Copyright (C) 2007-2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libhtp
PKG_VERSION:=0.5.0
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/OISF/libhtp.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=0.5.x
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2.0

PKG_BUILD_DEPENDS:=libiconv-full

include $(INCLUDE_DIR)/package.mk


CONFIGURE_ARGS += --disable-gccprotect
TARGET_CFLAGS += -I$(STAGING_DIR)/usr/lib/libiconv-full/include -DICONV_CONST=
TARGET_LDFLAGS += -L$(STAGING_DIR)/usr/lib/libiconv-full/lib

#TARGET_LDFLAGS += -liconv

define Package/libhtp
  SECTION:=libs
  CATEGORY:=Librarier
  TITLE:=HTP lib
  DEPENDS:=+libiconv-full +zlib
endef

define Build/InstallDev
	$(CP) $(PKG_INSTALL_DIR)/* $(1)/
endef

define Package/libhtp/install
	echo $(PKG_INSTALL_DIR)
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libhtp*.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libhtp))
