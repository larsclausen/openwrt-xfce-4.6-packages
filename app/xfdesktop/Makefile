#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=xfdesktop
PKG_VERSION:=4.5.91
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.tx-us.xfce.org/archive/xfce-$(PKG_VERSION)/src/
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib

define Package/xfdesktop
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=xfdesktop
  DEPENDS:=+libxfce4util +libxfcegui4 +libxfconf +libwnck +libglade
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Package/xfdesktop/install
	$(INSTALL_DIR) $(1)/etc/xdg/menus
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/etc/xdg/menus/* \
		$(1)/etc/xdg/menus/

	$(INSTALL_DIR) $(1)/usr/lib/xfce4/modules
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/xfce4/modules/*.{so*,a} \
		$(1)/usr/lib/xfce4/modules/

	$(INSTALL_DIR) $(1)/usr/lib/xfce4/panel-plugins
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/xfce4/panel-plugins/* \
		$(1)/usr/lib/xfce4/panel-plugins/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/icons/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/* \
		$(1)/usr/share/icons/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/* \
		$(1)/usr/share/pixmaps/

	$(INSTALL_DIR) $(1)/usr/share/xfce4/{backdrops,panel-plugins}
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/xfce4/{backdrops,panel-plugins} \
		$(1)/usr/share/xfce4/

	$(INSTALL_DIR) $(1)/usr/share/desktop-directories
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/desktop-directories/* \
		$(1)/usr/share/desktop-directories/

	$(INSTALL_DIR) $(1)/usr/share/applications
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications/
endef

$(eval $(call BuildPackage,xfdesktop))
