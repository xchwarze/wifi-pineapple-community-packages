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

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/zerbea/hcxtools.git
PKG_SOURCE_VERSION:=fd866a1003bf7380c3cbf925dceaabdb47d02832

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
	Portable solution for conversion of cap/pcap/pcapng (gz compressed) WiFi dump files to hashcat formats
	and to John the Ripper formats. hcx: h = hash, c = convert and calculate candidates, x = different hashtypes
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
