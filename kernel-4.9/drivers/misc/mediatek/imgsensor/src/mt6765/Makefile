# Copyright (C) 2015 MediaTek Inc.
# Updated Chipset Makefile for Oppo A31 (19581)

MTK_PLATFORM := mt6765
ARCH_MTK_PROJECT := oppo6765_19581
IMGSENSOR_DRIVER_PATH := $(srctree)/drivers/misc/mediatek/imgsensor/src
COMMON_VERSION := v1

# Header Paths for Common Drivers
subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/common/$(COMMON_VERSION)

# Link Common Files (Ensure no duplicates here)
obj-y += ../common/$(COMMON_VERSION)/imgsensor.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_hw.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_i2c.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_legacy.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_proc.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_sensor_list.o

# System Clock
obj-y += imgsensor_clk.o

# Jump into the Project Folder where the Deep Search happens
obj-y += camera_project/$(ARCH_MTK_PROJECT)/
