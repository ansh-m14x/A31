# Copyright (C) 2015 MediaTek Inc.
# Updated for Oppo A31 (19581) - Header Fix

subdir-ccflags-y += -I$(srctree)/drivers/i2c/busses/ \
             -I$(srctree)/drivers/misc/mediatek/ccu/inc \
             -I$(srctree)/drivers/misc/hqdevinfo

MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))
ARCH_MTK_PROJECT := $(subst ",,$(CONFIG_ARCH_MTK_PROJECT))

MTK_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek
PROJ_PATH := $(MTK_DRIVER_PATH)/imgsensor/src/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)

subdir-ccflags-y += -I$(MTK_DRIVER_PATH)/camera/$(MTK_PLATFORM) \
             -I$(MTK_DRIVER_PATH)/imgsensor/inc \
             -I$(PROJ_PATH)/camera_hw \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/$(MTK_PLATFORM)/camera_hw \
             -I$(MTK_DRIVER_PATH)/cam_cal/inc \
             -I$(MTK_DRIVER_PATH)/smi \
             -I$(MTK_DRIVER_PATH)/include/mt-plat/$(MTK_PLATFORM)/include/mach \
             -I$(PROJ_PATH)/back \
             -I$(PROJ_PATH)/front \
             -I$(PROJ_PATH)/back_aux

CUSTOM_KERNEL_FLAGS := $(addprefix -D, $(shell echo \
             $(CONFIG_CUSTOM_KERNEL_IMGSENSOR) | tr a-z A-Z))
subdir-ccflags-y += $(CUSTOM_KERNEL_FLAGS)

obj-y += $(subst ",,$(CONFIG_MTK_PLATFORM))/
