#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=libexo
PKG_VERSION:=0.3.91
PKG_RELEASE:=1

PKG_SOURCE:=exo-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://www.tx-us.xfce.org/archive/xfce-4.5.91/src/
PKG_MD5SUM:=
PKG_BUILD_DIR:=$(BUILD_DIR)/exo-$(PKG_VERSION)/
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib/

define Package/libexo
  SECTION:=xorg-framework
  CATEGORY:=Xorg
  SUBMENU:=framework
  TITLE:=libexo
  DEPENDS:=+gtk2 +libxfce4util +p5-uri
endef

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-hal \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR)	$(1)/usr/{lib/pkgconfig,include/exo-0.3}
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/exo-0.3/* \
		$(1)/usr/include/exo-0.3/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{la,so*,a} \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/libexo/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/

	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/lib/exo-helper-0.3 \
		$(PKG_INSTALL_DIR)/usr/lib/exo-compose-mail-0.3 \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/* \
		$(1)/usr/bin/

	$(INSTALL_DIR) $(1)/usr/share/icons/hicolor
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/hicolor/* \
		$(1)/usr/share/icons/hicolor

	$(INSTALL_DIR) $(1)/usr/share/pixmaps/exo-0.3
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/pixmaps/exo-0.3/* \
		$(1)/usr/share/pixmaps/exo-0.3/

endef

$(eval $(call BuildPackage,libexo))
