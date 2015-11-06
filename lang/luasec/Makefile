#
# Copyright (C) 2009-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=luasec
PKG_VERSION:=0.5
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/brunoos/luasec/archive/
PKG_MD5SUM:=0518f4524f399f33424c6f450e1d06db
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_NAME)-$(PKG_VERSION)

MAINTAINER:=W. Michael Petullo <mike@flyn.org>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/luasec
  SUBMENU:=Lua
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=LuaSec
  URL:=https://github.com/brunoos/luasec
  DEPENDS:=+lua +libopenssl +luasocket
endef

define Package/luasec/description
  LuaSec is a binding for OpenSSL library to provide TLS/SSL communication.
endef

define Build/Configure
endef

MAKE_FLAGS += \
	INCDIR="$(TARGET_CPPFLAGS) -I." \
	LIBDIR="$(TARGET_LDFLAGS) -L./luasocket" \
	LUACPATH="/opt/lib/lua" \
	LUAPATH="/opt/lib/lua"

define Build/Compile
$(call Build/Compile/Default,linux)
endef

define Package/luasec/install
	$(INSTALL_DIR) $(1)/opt/lib/lua
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/opt/lib/lua/ssl.so $(1)/opt/lib/lua/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/opt/lib/lua/ssl.lua $(1)/opt/lib/lua/
	$(INSTALL_DIR) $(1)/opt/lib/lua/ssl
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/opt/lib/lua/ssl/https.lua $(1)/opt/lib/lua/ssl/
endef

$(eval $(call BuildPackage,luasec))