# SPDX-License-Identifier: GPL-2.0-only
#
# Copyright (C) 2006-2011 OpenWrt.org

include $(TOPDIR)/rules.mk

ARCH:=loongarch64
BOARD:=loongarch64
BOARDNAME:=loongarch64
FEATURES:=squashfs ext4 vdi vmdk vhdx pcmcia targz fpu boot-part rootfs-part
SUBTARGETS:=generic

KERNEL_PATCHVER:=6.6

KERNELNAME:=vmlinux.efi

include $(INCLUDE_DIR)/target.mk

DEFAULT_PACKAGES += \
	partx-utils mkf2fs \
	e2fsprogs kmod-button-hotplug \
	grub2-bios-setup

$(eval $(call BuildTarget))

$(eval $(call $(if $(CONFIG_ISO_IMAGES),SetupHostCommand,Ignore),mkisofs, \
	Please install mkisofs. , \
	mkisofs -v 2>&1 , \
	genisoimage -v 2>&1 | grep genisoimage, \
	xorrisofs -v 2>&1 | grep xorriso \
))
