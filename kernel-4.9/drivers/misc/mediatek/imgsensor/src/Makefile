# Copyright (C) 2015 MediaTek Inc.
# Forced Override for Oppo A31 (19581) - Fixes Black Camera/Green Video

subdir-ccflags-y += -I$(srctree)/drivers/i2c/busses/ \
             -I$(srctree)/drivers/misc/mediatek/ccu/inc \
             -I$(srctree)/drivers/misc/hqdevinfo

# MANUALLY DEFINING TARGET TO PREVENT BUILD OVERLAP
MTK_PLATFORM       := mt6765
ARCH_MTK_PROJECT   := oppo6765_19581

MTK_PLATFORM_PATH_ROOT := $(srctree)/drivers/misc/mediatek/mach/mt6765
MTK_PROJECT_PATH_ROOT  := $(srctree)/drivers/misc/mediatek/mach/mt6765/oppo6765_19581

# Hard-set the sensor platform to mt6765
CONFIG_MTK_PLATFORM_SENSOR := mt6765

subdir-ccflags-y += -I$(MTK_PROJECT_PATH_ROOT)/camera/camera

MTK_DRIVER_PATH  := $(srctree)/drivers/misc/mediatek

# Explicitly link to the 19581 hardware folder
subdir-ccflags-y += -I$(MTK_DRIVER_PATH)/camera/mt6765 \
             -I$(MTK_DRIVER_PATH)/imgsensor/inc \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/mt6765/camera_project/oppo6765_19581/camera_hw \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/mt6765/camera_hw \
             -I$(MTK_DRIVER_PATH)/cam_cal/inc \
             -I$(MTK_DRIVER_PATH)/smi \
             -I$(MTK_DRIVER_PATH)/include/mt-plat/mt6765/include/mach \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/mt6765

CUSTOM_KERNEL_FLAGS := $(addprefix -D, $(shell echo \
             $(CONFIG_CUSTOM_KERNEL_IMGSENSOR) | tr a-z A-Z))
subdir-ccflags-y += $(CUSTOM_KERNEL_FLAGS)

# FORCE THE COMPILER TO ONLY USE MT6765 DIRECTORY
obj-y += mt6765/
