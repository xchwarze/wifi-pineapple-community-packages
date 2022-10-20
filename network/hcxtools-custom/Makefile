#
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
# Copyright (C) 2022 DSR! <xchwarze@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=hcxtools-custom
PKG_VERSION:=6.2.5
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/zerbea/hcxtools/tar.gz/$(PKG_VERSION)?
PKG_HASH:=27b1b1ad722b9d82f8e92c6bec92d081159e5b8225bd2a477bf8d304ff4aeb03

PKG_MAINTAINER:=DSR! <xchwarze@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=license.txt

include $(INCLUDE_DIR)/package.mk

define Package/hcxtools-custom
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libpthread +zlib +libcurl +libpcap +libopenssl
  TITLE:=hcxtools-custom
  URL:=https://github.com/zerbea/hcxtools
  SUBMENU:=Wireless
endef

define Package/hcxtools-custom/description
  Set of tools convert packets from captures (h = hash, c = capture, convert and calculate candidates, x = different hashtypes)
  for the use with latest hashcat or John the Ripper.
endef

define Build/Compile
  $(MAKE) -C $(PKG_BUILD_DIR)/ \
    $(TARGET_CONFIGURE_OPTS) \
    CFLAGS="$(TARGET_CFLAGS)"
endef

define Package/hcxtools-custom/install
  $(INSTALL_DIR) $(1)/sbin
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxpcapngtool                $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxhashtool                  $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxpsktool                   $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxpmktool                   $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxeiutool                   $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxwltool                    $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxhash2cap                  $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/wlancap2wpasec               $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/whoismac                     $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/usefulscripts/hcxgrep.py     $(1)/sbin/

  # Deprecated Tools Below
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxmactool                   $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxessidtool                 $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxpmkidtool                 $(1)/sbin/
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/hcxhashcattool               $(1)/sbin/
endef

$(eval $(call BuildPackage,hcxtools-custom))
