#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=gtk-xfce-engine
PKG_VERSION:=2.5.91
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.tx-us.xfce.org/archive/xfce-4.5.91/src/
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib \

define Package/gtk-xfce-engine
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=gtk-xfce-engine
  DEPENDS:=+gtk2
endef

define Package/gtk-xfce-engine/install
	$(INSTALL_DIR) $(1)/usr/lib/gtk-2.0/2.10.0/engines
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/gtk-2.0/2.10.0/engines/*.{so*,a} \
		$(1)/usr/lib/gtk-2.0/2.10.0/engines/

	$(INSTALL_DIR) $(1)/usr/share/themes
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/themes/* \
		$(1)/usr/share/themes
endef

$(eval $(call BuildPackage,gtk-xfce-engine))
