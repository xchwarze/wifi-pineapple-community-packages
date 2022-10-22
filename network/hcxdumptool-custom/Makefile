#
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
# Copyright (C) 2022 DSR! <xchwarze@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxdumptool-custom
PKG_VERSION:=6.2.5
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zerbea/hcxdumptool.git
PKG_SOURCE_VERSION:=e0b4199eb4c083ddd6d6ff9e69c4cdc041b8b83e

PKG_MAINTAINER:=DSR! <xchwarze@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=license.txt

include $(INCLUDE_DIR)/package.mk

define Package/hcxdumptool-custom
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libpcap +libopenssl
	TITLE:=hcxdumptool-custom
	URL:=https://github.com/zerbea/hcxdumptool
	SUBMENU:=Wireless
endef

define Package/hcxdumptool-custom/description
	Small tool to capture packets from wlan devices. After capturing, upload
	the "uncleaned" cap here (https://wpa-sec.stanev.org/?submit)
	to see if your ap or the client is vulnerable by using common wordlists.
	Convert the cap to hccapx and/or to WPA-PMKID-PBKDF2 hashline (16800) with hcxpcaptool (hcxtools)
	and check if wlan-key or plainmasterkey was transmitted unencrypted.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)/ \
		$(TARGET_CONFIGURE_OPTS) \
		CFLAGS="$(TARGET_CFLAGS)"
endef

define Package/hcxdumptool-custom/install
	$(INSTALL_DIR)  $(1)/sbin
	$(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxdumptool  $(1)/sbin/
endef

$(eval $(call BuildPackage,hcxdumptool-custom))
