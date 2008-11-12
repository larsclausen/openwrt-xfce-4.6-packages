#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12225 2008-08-06 22:10:29Z nbd $

include $(TOPDIR)/rules.mk

PKG_NAME:=tango-icon-theme
PKG_VERSION:=0.8.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://tango.freedesktop.org/releases/
#PKG_MD5SUM:=dee233bf288ee795ac96a98cc2e369b6

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL=1

define Package/tango-icon-theme
  SECTION:=xorg-data
  CATEGORY:=Xorg
  SUBMENU:=Data
  TITLE:=Tango icon theme
  URL:=http://tango.freedesktop.org/
endef

define Build/Configure
	$(call Build/Configure/Default, \
	    --disable-icon-framing \
	)
endef

define Package/tango-icon-theme/install
	$(INSTALL_DIR) $(1)/usr/share/icons
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/icons/* \
		$(1)/usr/share/icons/
endef

$(eval $(call BuildPackage,tango-icon-theme))
