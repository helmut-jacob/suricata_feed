
# Copyright (C) 2007-2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=suricata
PKG_VERSION:=2.0.8
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/inliniac/suricata.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=15dd771fdc1539bce2fc8dc34b95f839265c8f89
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

CONFIGURE_ARGS += --enable-non-bundled-htp --disable-gccprotect

TARGET_LDFLAGS += -L$(STAGING_DIR)/usr/lib/libiconv-full/lib -liconv -lssp

define Package/suricata
  SECTION:=net
  CATEGORY:=Network
  TITLE:=IPS
  DEPENDS:=+libpcre +libyaml +libhtp +libmagic +libssp +libpthread +libpcap
endef

define Package/suricata/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/suricata* $(1)/usr/bin
endef

$(eval $(call BuildPackage,suricata))
