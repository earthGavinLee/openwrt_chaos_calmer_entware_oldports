#
# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=keynote
PKG_VERSION:=2.3
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://downloads.openwrt.org/sources/
PKG_MD5SUM:=b569066ac2ba1356c2112b118a7d74d0

PKG_BUILD_PARALLEL:=0

include $(INCLUDE_DIR)/package.mk

define Package/keynote
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=+libopenssl
  TITLE:=Simple and flexible trust-management system
  URL:=http://www1.cs.columbia.edu/~angelos/keynote.html
endef

define Package/keynote/description
 KeyNote is a simple and flexible trust-management system designed to work
 well for a variety of large- and small- scale Internet-based applications.
 It provides a single, unified language for both local policies and
 credentials.
endef

CONFIGURE_ARGS += \
	--enable-static \
	--enable-shared

MAKE_FLAGS += \
	CFLAGS="$(TARGET_CFLAGS)"

define Build/InstallDev
	$(INSTALL_DIR) $(1)/opt/include/keynote
	$(CP) $(PKG_BUILD_DIR)/{assertion,header,keynote,signature}.h $(1)/opt/include/keynote/
	$(INSTALL_DIR) $(1)/opt/lib
	$(CP) $(PKG_BUILD_DIR)/libkeynote.a $(1)/opt/lib/
endef

define Package/keynote/install
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/keynote $(1)/opt/sbin/
endef

$(eval $(call BuildPackage,keynote))
