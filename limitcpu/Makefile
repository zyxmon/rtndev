#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=limitcpu
PKG_VERSION:=2.2
PKG_RELEASE:=1

PKG_SOURCE:=cpulimit-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)
PKG_MD5SUM:=96b67b38b5f0b3495e3d748db422d176

PKG_BUILD_DIR:=$(BUILD_DIR)/cpulimit-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/limitcpu
	SECTION:=utils
	CATEGORY:=Utilities
	SUBMENU:=CPU tools
	DEPENDS:=+librt
	TITLE:=CPU usage limiter
	URL:=http://limitcpu.sourceforge.net
	MAINTAINER:=Entware team, entware.wl500g.info
endef

define Package/limitcpu/description
 LimitCPU is a program to throttle the CPU cycles used by other applications.
 It will monitor a process and make sure its CPU usage stays at or below
 a given percentage.
endef

define Package/limitcpu/install
	$(INSTALL_DIR) $(1)/opt/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/cpulimit $(1)/opt/bin/
endef

$(eval $(call BuildPackage,limitcpu))
