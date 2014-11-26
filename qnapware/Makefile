#
# Copyright (C) 2011-2014 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qnapware
PKG_VERSION:=2.6.1
PKG_RELEASE:=5

include $(INCLUDE_DIR)/package.mk

define Package/qnapware
	SECTION:=libs
	CATEGORY:=Libraries
	DEPENDS:=+libc +libgcc +libstdcpp +libpthread +librt +findutils
	TITLE:=provides basic toolchain libraries (dummy)
	MAINTAINER:=Zyxmon
endef

define Package/qnapware/description
 qnapware is a metapackage to install qnapware basic libraries and scripts.
endef

define Build/Prepare
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/qnapware/install
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/rc.unslung $(1)/opt/etc/init.d/
	$(INSTALL_DATA) ./files/rc.func $(1)/opt/etc/init.d/
	$(INSTALL_BIN) ./files/profile $(1)/opt/etc/
endef

define Package/qnapware/conffiles
/opt/etc/profile
endef

$(eval $(call BuildPackage,qnapware))
