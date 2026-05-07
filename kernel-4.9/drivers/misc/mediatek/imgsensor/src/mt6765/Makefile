# Copyright (C) 2015 MediaTek Inc.
# Corrected mt6765 Makefile - No Duplicates

MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))
ARCH_MTK_PROJECT := $(subst ",,$(CONFIG_ARCH_MTK_PROJECT))
IMGSENSOR_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek/imgsensor/src
COMMON_VERSION := v1

subdir-ccflags-y +=  -I$(IMGSENSOR_DRIVER_PATH)/common/$(COMMON_VERSION)

# Link Common Files - FIXED: Only one instance per file
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

# Handle Project Specific Hardware
ifeq (,$(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/camera_hw))
  subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_hw
  obj-y += camera_hw/
  ifneq ($(project_drv),)
    obj-y += camera_project/$(ARCH_MTK_PROJECT)/
  endif
else
  obj-y += camera_project/$(ARCH_MTK_PROJECT)/
  subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/camera_hw
endif
