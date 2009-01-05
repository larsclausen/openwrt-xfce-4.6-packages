include $(TOPDIR)/rules.mk

PKG_NAME:=libglade
PKG_VERSION:=2.6.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.6
PKG_MD5SUM:=da4f9d1c6cd1337f6ef5e2db768d8557
PKG_FIXUP:=libtool

include $(INCLUDE_DIR)/package.mk

PKG_INSTALL:=1

EXTRA_CFLAGS+=-I$(STAGING_DIR)/usr/lib/libintl/include \
		      -I$(STAGING_DIR)/usr/libiconv/include

EXTRA_LDFLAGS+=-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
		       -L$(STAGING_DIR)/usr/lib/libintl/lib/ \
			   -L$(STAGING_DIR)/usr/lib/libiconv/lib/

define Package/libglade
  SECTION:=xorg-libs
  CATEGORY:=Xorg
  SUBMENU:=libraries
  TITLE:=libglade
  URL:=http://www.jamesh.id.au/software/libglade/
  DEPENDS:=+libxml2 +gtk2
endef

define Build/Configure
	$(call Build/Configure/Default, \
	    --disable-gtktest \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib/pkgconfig,include/libglade-2.0/glade}

	$(CP) \
	    $(PKG_INSTALL_DIR)/usr/lib/libglade-2.0.{so*,la,a} \
	    $(1)/usr/lib/

	$(INSTALL_DATA) \
	    $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
	    $(1)/usr/lib/pkgconfig/
	$(SED) \
		's,^moduledir=$$$${libdir},moduledir=/usr/lib,g' \
		$(1)/usr/lib/pkgconfig/libglade-2.0.pc

	$(INSTALL_DATA) \
	    $(PKG_INSTALL_DIR)/usr/include/libglade-2.0/glade/*.h \
	    $(1)/usr/include/libglade-2.0/glade/
endef

define Package/libglade/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
	    $(PKG_INSTALL_DIR)/usr/lib/libglade-2.0.so* \
	    $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libglade))


