# Copyright (C) 2015 MediaTek Inc.
# Updated Src Makefile with Deep Folder Header Support

# Basic Mediatek Includes
subdir-ccflags-y += -I$(srctree)/drivers/i2c/busses/ \
             -I$(srctree)/drivers/misc/mediatek/ccu/inc \
             -I$(srctree)/drivers/misc/hqdevinfo

MTK_PLATFORM     := mt6765
ARCH_MTK_PROJECT := oppo6765_19581
MTK_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek
PROJ_SRC_PATH    := $(MTK_DRIVER_PATH)/imgsensor/src/$(MTK_PLATFORM)/camera_project/$(ARCH_MTK_PROJECT)

# Header Search Paths - Including Deep Folders from your Photos
subdir-ccflags-y += -I$(MTK_DRIVER_PATH)/camera/$(MTK_PLATFORM) \
             -I$(MTK_DRIVER_PATH)/imgsensor/inc \
             -I$(PROJ_SRC_PATH)/camera_hw \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/$(MTK_PLATFORM)/camera_hw \
             -I$(MTK_DRIVER_PATH)/cam_cal/inc \
             -I$(MTK_DRIVER_PATH)/smi \
             -I$(MTK_DRIVER_PATH)/include/mt-plat/$(MTK_PLATFORM)/include/mach \
             -I$(PROJ_SRC_PATH)/back \
             -I$(PROJ_SRC_PATH)/front \
             -I$(PROJ_SRC_PATH)/back_aux

# Convert sensors list to compiler flags
CUSTOM_KERNEL_FLAGS := $(addprefix -D, $(shell echo \
             $(CONFIG_CUSTOM_KERNEL_IMGSENSOR) | tr a-z A-Z))
subdir-ccflags-y += $(CUSTOM_KERNEL_FLAGS)

# Enter the chipset directory
obj-y += mt6765/
