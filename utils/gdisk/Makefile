#
# Copyright (C) 2011-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gptfdisk
PKG_VERSION:=0.8.8
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/gptfdisk
PKG_MD5SUM:=bd47d03ec27bab5613254b5a20f72143

PKG_BUILD_DEPENDS:=libncurses libpopt libuuid

include $(INCLUDE_DIR)/package.mk

define Package/gdisk/Default
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=disc
  URL:=http://www.rodsbooks.com/gdisk/
  DEPENDS:=+libstdcpp
endef

define Package/gdisk
  $(call Package/gdisk/Default)
  DEPENDS+= +libuuid
  TITLE:=GUID partition table manipulation utility
endef

define Package/gdisk/description
  This package contains a utility for managing Globally Unique Identifier (GUID)
  Partition Table (GPT) disks.
endef

define Package/cgdisk
  $(call Package/gdisk/Default)
  DEPENDS+= +libncurses +libuuid
  TITLE:=GUID partition table manipulation utility
endef

define Package/cgdisk/description
  This package contains a utility for managing Globally Unique Identifier (GUID)
  Partition Table (GPT) disks.
endef

define Package/sgdisk
  $(call Package/gdisk/Default)
  DEPENDS+= +libpopt +libuuid
  TITLE:=GUID partition table manipulation utility (Command-line)
endef

define Package/sgdisk/description
  This package contains a utility for managing Globally Unique Identifier (GUID)
  Partition Table (GPT) disks using command-line only.
endef

define Package/fixparts
  $(call Package/gdisk/Default)
  TITLE:=MBR partition table repair utility
endef

define Package/fixparts/description
  This package contains a utility for repairing certain types of problems with
  Master Boot Record (MBR) partition tables.
endef

define Package/gdisk/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/gdisk $(1)/sbin/
endef

define Package/cgdisk/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/cgdisk $(1)/sbin/
endef

define Package/sgdisk/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/sgdisk $(1)/sbin/
endef

define Package/fixparts/install
	$(INSTALL_DIR) $(1)/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/fixparts $(1)/sbin/
endef

$(eval $(call BuildPackage,gdisk))
$(eval $(call BuildPackage,cgdisk))
$(eval $(call BuildPackage,sgdisk))
$(eval $(call BuildPackage,fixparts))
