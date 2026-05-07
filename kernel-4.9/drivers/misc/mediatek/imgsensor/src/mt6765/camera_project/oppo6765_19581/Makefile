# Copyright (C) 2017 MediaTek Inc.
# Deep Search Fix for 19581 Subfolders

MTK_PLATFORM := $(subst ",,$(CONFIG_MTK_PLATFORM))
ARCH_MTK_PROJECT := $(subst ",,$(CONFIG_ARCH_MTK_PROJECT))
IMGSENSOR_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek/imgsensor/src

define FILTER_PROJECT_DRV
# Search Root
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/$(1)),)
  project_drv += $(1)/
endif
# Search Back
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/back/$(1)),)
  project_drv += back/$(1)/
endif
# Search Front
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/front/$(1)),)
  project_drv += front/$(1)/
endif
# Search Back_Aux
ifneq ($(wildcard $(IMGSENSOR_DRIVER_PATH)/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)/back_aux/$(1)),)
  project_drv += back_aux/$(1)/
endif
endef

obj-y += camera_hw/

$(foreach drv,$(subst $\",,$(CONFIG_CUSTOM_KERNEL_IMGSENSOR)),$(eval $(call FILTER_PROJECT_DRV,$(drv))))

obj-y += $(project_drv)

ifneq ($(project_drv),)
$(info imgsensor drv by project deep-search: $(project_drv))
endif

