#
# Copyright (C) 2008-2010 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gtkmm
PKG_VERSION:=2.16.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@GNOME/$(PKG_NAME)/2.16
PKG_MD5SUM:=a82e3b5b93008421ff67df16d1e51ec2

PKG_FIXUP:=libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

TARGET_LDFLAGS+=\
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib

define Package/gtkmm
  SECTION:=xorg-framework
  CATEGORY:=Xorg
  SUBMENU:=framework
  TITLE:=GTK+-2.0
  DEPENDS:=+gtk2 +cairomm +pangomm +glibmm
  URL:=http://www.gtkmm.org/
endef

CONFIGURE_ARGS+= --disable-docs --disable-demos

define Build/InstallDev
	$(INSTALL_DIR) \
		$(1)/usr/lib/pkgconfig \
		$(1)/usr/include

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/* \
		$(1)/usr/include/

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/* \
		$(1)/usr/lib/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/gtkmm/install
	$(INSTALL_DIR) \
		$(1)/usr/lib

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,gtkmm))
