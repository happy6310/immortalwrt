include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-athena-led
PKG_VERSION:=0.0.7
PKG_RELEASE:=20241029

LUCI_TITLE:=LuCI Support for athena-led
LUCI_DEPENDS:=

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  TITLE:=$(LUCI_TITLE)
endef

define Package/$(PKG_NAME)/description
  LuCI support for athena-led
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	$(CP) ./luasrc/* $(1)/usr/lib/lua/luci/
	$(INSTALL_DIR) $(1)/
	$(CP) ./root/* $(1)/
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh
[ -n "$$IPKG_INSTROOT" ] || {
	chmod +x /usr/sbin/athena-led
	chmod +x /etc/init.d/athena_led
}
exit 0
endef

include $(TOPDIR)/feeds/luci/luci.mk

$(eval $(call BuildPackage,$(PKG_NAME)))
