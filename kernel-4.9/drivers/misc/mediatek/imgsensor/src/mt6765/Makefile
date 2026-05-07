# Copyright (C) 2015 MediaTek Inc.
# Cleaned mt6765 Base - Removed Duplicates

MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))
ARCH_MTK_PROJECT := $(subst ",,$(CONFIG_ARCH_MTK_PROJECT))
IMGSENSOR_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek/imgsensor/src
COMMON_VERSION := v1

subdir-ccflags-y +=  -I$(IMGSENSOR_DRIVER_PATH)/common/$(COMMON_VERSION)

# FIXED: imgsensor.o only appears ONCE now
obj-y += ../common/$(COMMON_VERSION)/imgsensor.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_hw.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_i2c.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_legacy.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_proc.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_sensor_list.o

define FILTER_DRV
ifeq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/$(1)),)
  ifeq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/$(1)),)
    common_drv += ../common/$(COMMON_VERSION)/$(1)/
  else
    platform_drv += $(1)/
  endif
else
  project_drv += ./camera_project/$(ARCH_MTK_PROJECT)/$(1)/
endif
endef

$(foreach drv,$(subst $\",,$(CONFIG_CUSTOM_KERNEL_IMGSENSOR)),$(eval $(call FILTER_DRV,$(drv))))

obj-y += $(common_drv)
obj-y += $(platform_drv)
obj-y += imgsensor_clk.o

# Jump to Project Folder
obj-y += camera_project/$(ARCH_MTK_PROJECT)/
subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/camera_hw
