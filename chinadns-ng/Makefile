include $(TOPDIR)/rules.mk

PKG_NAME:=chinadns-ng
PKG_VERSION:=1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zfl9/chinadns-ng.git
PKG_SOURCE_VERSION:=master
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION)

PKG_LICENSE:=GPLv3
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=pexcn <i@pexcn.me>

include $(INCLUDE_DIR)/package.mk

define Package/chinadns-ng
	SECTION:=net
	CATEGORY:=Network
	TITLE:=ChinaDNS next generation, refactoring with epoll and ipset
	URL:=https://github.com/zfl9/chinadns-ng
	DEPENDS:=+ipset
endef

define Package/chinadns-ng/description
ChinaDNS next generation, refactoring with epoll and ipset.
endef

define Package/chinadns-ng/conffiles
/etc/chinadns-ng/chnlist.txt
/etc/chinadns-ng/gfwlist.txt
/etc/chinadns-ng/chnroute.ipset
/etc/chinadns-ng/chnroute6.ipset
endef

define Package/chinadns-ng/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/chinadns-ng
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/chinadns-ng $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/update-chnlist.sh $(1)/etc/chinadns-ng
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/update-gfwlist.sh $(1)/etc/chinadns-ng
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/update-chnroute.sh $(1)/etc/chinadns-ng
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/update-chnroute6.sh $(1)/etc/chinadns-ng
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/chnlist.txt $(1)/etc/chinadns-ng
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/gfwlist.txt $(1)/etc/chinadns-ng
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/chnroute.ipset $(1)/etc/chinadns-ng
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/chnroute6.ipset $(1)/etc/chinadns-ng
	chmod +x ./files/*
	$(CP) ./files/* $(1)/etc/chinadns-ng
endef

$(eval $(call BuildPackage,chinadns-ng))
