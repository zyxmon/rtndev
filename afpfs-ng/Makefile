#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=afpfs-ng
PKG_VERSION:=0.8.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=@SF/$(PKG_NAME)/$(PKG_NAME)/$(PKG_VERSION)
PKG_MD5SUM:=1bdd9f8a06e6085ea4cc38ce010ef60b

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/afpfs-ng
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Filesystem
	DEPENDS:=+libfuse +libgcrypt +libgmp +libncurses +libreadline
	TITLE:=a client for Apple Filing Protocol
	URL:=https://sites.google.com/site/alexthepuffin/home
	MAINTAINER:=Entware team, entware.wl500g.info
endef

define Package/afpfs-ng/description
 afpfs-ng is an Apple Filing Protocol client that will allow BSD, Linux
 and Mac OS X systems to access files exported from a Mac OS system with
 AFP over TCP.
endef

define Package/afpfs-ng/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/Apps/opt/bin/afp{cmd,fs,fsd,getstatus} \
	    $(PKG_INSTALL_DIR)/Apps/opt/bin/mount_afp \
	    $(1)/opt/bin/
	$(LN) -s /Apps/opt/bin/mount_afp $(1)/opt/bin/afp_client
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_INSTALL_DIR)/Apps/opt/lib/libafpclient.so* $(1)/opt/lib/
endef

$(eval $(call BuildPackage,afpfs-ng))
