#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=thunar
PKG_VERSION:=0.9.91
PKG_RELEASE:=1

PKG_SOURCE:=Thunar-$(PKG_VERSION).tar.bz2
PKG_BUILD_DIR:=$(BUILD_DIR)/Thunar-$(PKG_VERSION)
PKG_SOURCE_URL:=http://www.tx-us.xfce.org/archive/xfce-4.5.91/src/
PKG_MD5SUM:=
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib

define Package/thunar
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=thunar
  DEPENDS:=+libexo +libpng +libxfce4util
endef

define Build/Configure
	$(call Build/Configure/Default, \
	)
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)
	$(MAKE) -C $(PKG_BUILD_DIR)/ install DESTDIR=$(PKG_INSTALL_DIR)
endef

define Build/InstallDev
	$(INSTALL_DIR)	$(1)/usr/{lib/pkgconfig,lib/xfce4/panel-plugins,lib/thunarx-1,include}
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{la,so*} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/thunarx-1/*.{la,so*} \
		$(1)/usr/lib/thunarx-1/

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/xfce4/panel-plugins/* \
		$(1)/usr/lib/xfce4/panel-plugins/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/thunar/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a} \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/icons
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/* \
		$(1)/usr/share/icons/

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/Thunar
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/Thunar/* \
		$(1)/usr/share/pixmaps/Thunar
endef

$(eval $(call BuildPackage,thunar))
