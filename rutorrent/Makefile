#
# Copyright (C) 2011-2015 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rutorrent
PKG_VERSION:=3.7
PKG_REV:=ac2db1536302bdc5b27aff6b15d54b0e9837fa59
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/Novik/ruTorrent
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk

RUTORRENT_PLUGINS := \
	autotools check_port chunks cookies cpuload create data datadir \
	diskspace edit erasedata extratio extsearch feeds filedrop \
	geoip _getdir history httprpc ipad loginmgr lookat mediainfo _noty \
	_noty2 ratio retrackers rpc rss rssurlrewrite rutracker_check scheduler \
	screenshots seedingtime show_peers_like_wtorrent source _task \
	theme throttle tracklabels trafic unpack

DEPENDS_screenshots = +ffmpeg
DEPENDS_unpack = +unrar

define Package/rutorrent/Default
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=BitTorrent
	DEPENDS:=+rtorrent-rpc +coreutils-stat +coreutils-id +gzip +curl
	TITLE:=Yet another web front-end for rTorrent
	URL:=$(PKG_SOURCE_URL)
	MAINTAINER:=Entware team, entware.wl500g.info
endef

define Package/rutorrent
	$(call Package/rutorrent/Default)
	TITLE:=Yet another web front-end for rTorrent
	MENU:=1
endef

define Package/rutorrent/description
 ruTorrent is a front-end for the popular Bittorrent client rTorrent.
endef

define GenPlugin
 define Package/$(1)
	$(call Package/rutorrent/Default)
	DEPENDS:=rutorrent $(DEPENDS_$(2))
	TITLE:=ruTorrent $(2) plugin
 endef

 define Package/$(1)/description
  This is a $(2) Rutorrent plugin.
 endef
endef

$(foreach a,$(RUTORRENT_PLUGINS),$(eval $(call GenPlugin,rutorrent-plugin-$(a),$(a))))

define Build/Configure
endef

define Build/Compile
endef

define Package/rutorrent/install
	$(INSTALL_DIR) $(1)/opt/share/www/rutorrent/plugins
	$(CP) $(PKG_BUILD_DIR)/{conf,css,images,js,lang,php,share,.htaccess,index.html} $(1)/opt/share/www/rutorrent/
endef

define BuildPlugin
  define Package/$(1)/install
	$(INSTALL_DIR) $$(1)/opt/share/www/rutorrent/plugins/$(2)
	$(CP) $(PKG_BUILD_DIR)/plugins/$(2)/* $$(1)/opt/share/www/rutorrent/plugins/$(2)/
  endef

  $$(eval $$(call BuildPackage,$(1)))
endef

$(eval $(call BuildPackage,rutorrent))
$(foreach a,$(RUTORRENT_PLUGINS),$(eval $(call BuildPlugin,rutorrent-plugin-$(a),$(a))))
