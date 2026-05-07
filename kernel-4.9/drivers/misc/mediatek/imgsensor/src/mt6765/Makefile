# Copyright (C) 2015 MediaTek Inc.

MTK_PLATFORM := mt6765
ARCH_MTK_PROJECT := oppo6765_19581
IMGSENSOR_DRIVER_PATH := $(srctree)/drivers/misc/mediatek/imgsensor/src
COMMON_VERSION := v1

# Link Common Files (Cleaned of duplicates to prevent Error 2)
subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/common/$(COMMON_VERSION)
obj-y += ../common/$(COMMON_VERSION)/imgsensor.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_hw.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_i2c.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_legacy.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_proc.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_sensor_list.o

# Filter Logic to find your specific 19581 sensor drivers
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

# Apply identified drivers
obj-y += $(common_drv)
obj-y += $(platform_drv)
obj-y += imgsensor_clk.o

# Force Oppo A31 Hardware and Project paths
subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/camera_hw
obj-y += camera_hw/
obj-y += camera_project/$(ARCH_MTK_PROJECT)/
