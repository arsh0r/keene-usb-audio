# 
# Copyright (C) 2010 Industrie Dial Face S.p.A.
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=keene
PKG_RELEASE:=1
PKG_VERSION:=0.2
PKG_FILE_DEPEND:=./src

include $(INCLUDE_DIR)/package.mk

define Package/keene
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=little USB FM Transmitter
  DEPENDS:=+libusb
  URL:=https://github.com/seidler2547/keene-usb-audio
endef

define Package/keene/description
Usage: keene tx pre chan freq pa enable mute
 The arguments correspond to
  - TX (0-23)
  - preemphasis (50us or 75us)
  - channels (mono or stereo)
  - frequency (floats from 76.0-108.0)
  - PA (30 to 120)
  - enable or disable
  - mute or unmute
 If one of the arguments is - the default value is set.
Example: keene 0 50us stereo 85.5f 120 enable unmute
endef

TARGET_CFLAGS += \
	-I$(PKG_BUILD_DIR) \
	-I$(PKG_BUILD_DIR)/include \
	-I$(STAGING_DIR)/usr/include

MAKE_FLAGS += \
	CONFIGURE_ARGS="$(CONFIGURE_ARGS)" \
	CFLAGS="$(TARGET_CFLAGS)"

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Configure
endef

define Package/keene/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/keene $(1)/usr/bin
endef

$(eval $(call BuildPackage,keene))
