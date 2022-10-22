#
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
# Copyright (C) 2022 DSR! <xchwarze@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxlabtools
PKG_VERSION:=6.2.7
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zerbea/wifi_laboratory.git
PKG_SOURCE_VERSION:=c699e319f64835feeb155cb4c340b4bfda43a5f0

PKG_MAINTAINER:=DSR! <xchwarze@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=license.txt

include $(INCLUDE_DIR)/package.mk

define Package/hcxlabtools
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libpcap +libopenssl
	TITLE:=hcxlabtools
	URL:=https://github.com/zerbea/wifi_laboratory
	SUBMENU:=Wireless
endef

define Package/hcxlabtools/description
	Skeleton to test WiFi adapters and to understand 802.11 protocol. 
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/ \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)"
endef

define Package/hcxlabtools/install
	$(INSTALL_DIR)  $(1)/sbin
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm1     $(1)/sbin/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm2     $(1)/sbin/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm1234  $(1)/sbin/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetmall   $(1)/sbin/
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabdumpall   $(1)/sbin/
endef

$(eval $(call BuildPackage,hcxlabtools))
