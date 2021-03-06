#
# Copyright (C) 2007-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rsync
PKG_VERSION:=3.0.9-git-1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=http://rsync.samba.org/ftp/rsync/src
#PKG_MD5SUM:=5ee72266fe2c1822333c407e1761b92b

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://git.samba.org/rsync.git
PKG_REV:=b55115ec6f127f7def2dfcc907bf6e28d775e53c
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/rsync
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=File Transfer
  TITLE:=Fast remote file copy program (like rcp)
  DEPENDS:=+libpopt
  URL:=http://rsync.samba.org/
endef

define Package/rsyncd
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=File Transfer
  TITLE:=Rsync daemon
  DEPENDS:=+rsync
endef

define Package/rsync/description
	rsync is a program that allows files to be copied to
	and from remote machines in much the same way as rcp.
	It has many more options than rcp, and uses the rsync
	remote-update protocol to greatly speed up file
	transfers when the destination file already exists.

	The rsync remote-update protocol allows rsync to
	transfer just the differences between two sets of files
	across the network link.
endef

CONFIGURE_ARGS += \
	--with-included-popt=no \
	--disable-debug \
	--disable-locale \
	--disable-xattr-support \
	--disable-acl-support \

define Package/rsync/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/$(PKG_NAME) $(1)/usr/bin/
endef

define Package/rsyncd/description
	rsyncd is a configuration file and initscript to
	utilize rsync as a daemon. It uses the same binary
	as rsync.
endef

define Package/rsyncd/conffiles
/etc/rsyncd.conf
endef

define Package/rsyncd/install
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) ./files/rsyncd.conf $(1)/etc/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/rsyncd.init $(1)/etc/init.d/rsyncd
endef

$(eval $(call BuildPackage,rsync))
$(eval $(call BuildPackage,rsyncd))
