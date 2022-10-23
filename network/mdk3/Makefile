#
# Copyright (C) 2009 OpenWrt.org
# Copyright (C) 2019 Andreas Nilsen <adde88@gmail.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mdk3
PKG_VERSION:=8.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aircrack-ng/mdk3.git
PKG_SOURCE_VERSION:=3be47e2e02d311e6746bd6d38c73ec957300aba0

PKG_MAINTAINER:=Andreas Nilsen <adde88@gmail.com>

include $(INCLUDE_DIR)/package.mk

define Package/mdk3
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libpthread +libnl +libpcap
	TITLE:=MDK3
	URL:=https://github.com/aircrack-ng/mdk3
	SUBMENU:=Wireless
endef

define Package/mdk3/description
	Tool to exploit wireless vulnerabilities
endef

TARGET_CFLAGS="-fPIC"

define Package/mdk3/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mdk3 $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,mdk3))
