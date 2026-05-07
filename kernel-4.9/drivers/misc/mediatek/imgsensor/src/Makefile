# Copyright (C) 2015 MediaTek Inc.
# FINAL PATH FIX FOR OPPO A31 (19581)

# Essential Header Paths
subdir-ccflags-y += -I$(srctree)/drivers/i2c/busses/ \
             -I$(srctree)/drivers/misc/mediatek/ccu/inc \
             -I$(srctree)/drivers/misc/hqdevinfo

# Force identity to ensure the mt6765 path is prioritized
MTK_PLATFORM       := mt6765
ARCH_MTK_PROJECT   := oppo6765_19581
MTK_DRIVER_PATH    := $(srctree)/drivers/misc/mediatek

# Project-Specific Header Inclusion
subdir-ccflags-y += -I$(MTK_DRIVER_PATH)/imgsensor/inc \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/mt6765/camera_hw \
             -I$(MTK_DRIVER_PATH)/imgsensor/src/mt6765/camera_project/oppo6765_19581 \
             -I$(MTK_DRIVER_PATH)/include/mt-plat/mt6765/include/mach

# Convert config sensors to compiler flags
CUSTOM_KERNEL_FLAGS := $(addprefix -D, $(shell echo \
             $(CONFIG_CUSTOM_KERNEL_IMGSENSOR) | tr a-z A-Z))
subdir-ccflags-y += $(CUSTOM_KERNEL_FLAGS)

# Traverse to the chipset folder
obj-y += mt6765/
