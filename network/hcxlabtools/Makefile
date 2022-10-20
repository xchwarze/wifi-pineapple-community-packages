#
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
# Copyright (C) 2022 DSR! <xchwarze@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxlabtool
PKG_VERSION:=6.2.5
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_URL:=https://github.com/zerbea/wifi_laboratory
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=698085830f4f2fa69fd675484f498c20009f1481

PKG_MAINTAINER:=DSR! <xchwarze@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=license.txt

include $(INCLUDE_DIR)/package.mk

define Package/hcxlabtool
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpcap +libopenssl
  TITLE:=hcxlabtool
  URL:=https://github.com/zerbea/wifi_laboratory
  SUBMENU:=Wireless
endef

define Package/hcxlabtool/description
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

define Package/hcxlabtool/install
  $(INSTALL_DIR)  $(1)/sbin
  $(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm1     $(1)/sbin/
  $(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm2     $(1)/sbin/
  $(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetm1234  $(1)/sbin/
  $(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabgetmall   $(1)/sbin/
  $(INSTALL_BIN)  $(PKG_BUILD_DIR)/hcxlabdumpall   $(1)/sbin/
endef

$(eval $(call BuildPackage,hcxlabtool))
