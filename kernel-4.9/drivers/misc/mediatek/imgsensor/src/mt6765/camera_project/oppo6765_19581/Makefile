# Copyright (C) 2017 MediaTek Inc.
# Fixed for Oppo A31 Deep Folder Structure

MTK_PLATFORM := mt6765
ARCH_MTK_PROJECT := oppo6765_19581
IMGSENSOR_DRIVER_PATH := $(srctree)/drivers/misc/mediatek/imgsensor/src

# Link Camera Hardware
obj-y += camera_hw/

# Custom Filter to look into subfolders
define FILTER_DEEP_DRV
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/back/$(1)),)
  project_drv += back/$(1)/
endif
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/front/$(1)),)
  project_drv += front/$(1)/
endif
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/back_aux/$(1)),)
  project_drv += back_aux/$(1)/
endif
endef

$(foreach drv,$(subst $\",,$(CONFIG_CUSTOM_KERNEL_IMGSENSOR)),$(eval $(call FILTER_DEEP_DRV,$(drv))))

obj-y += $(project_drv)

ifneq ($(project_drv),)
$(info imgsensor drv by project deep-search: $(project_drv))
endif
