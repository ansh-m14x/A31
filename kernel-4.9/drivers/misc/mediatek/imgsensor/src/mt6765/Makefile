# Copyright (C) 2015 MediaTek Inc.
# Corrected mt6765 Makefile - Path Fix for back/front/back_aux

MTK_PLATFORM := mt6765
ARCH_MTK_PROJECT := oppo6765_19581
IMGSENSOR_DRIVER_PATH := $(srctree)/drivers/misc/mediatek/imgsensor/src
COMMON_VERSION := v1

# Header Paths
subdir-ccflags-y += -I$(IMGSENSOR_DRIVER_PATH)/common/$(COMMON_VERSION)

# Link Common Files (Exactly once)
obj-y += ../common/$(COMMON_VERSION)/imgsensor.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_hw.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_i2c.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_legacy.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_proc.o
obj-y += ../common/$(COMMON_VERSION)/imgsensor_sensor_list.o

# HARD-CODED PROJECT PATHS (Injected from your photo evidence)
PROJECT_PATH := camera_project/oppo6765_19581

# Main Camera
obj-y += $(PROJECT_PATH)/back/ov12a10_st_mipi_raw/
# Front Camera
obj-y += $(PROJECT_PATH)/front/hi846_mipi_raw/
# Macro/Depth
obj-y += $(PROJECT_PATH)/back_aux/ov12a10_qtech_mipi_raw/
obj-y += $(PROJECT_PATH)/back_aux/gc2375h_mipi_raw/

# System Logic
obj-y += imgsensor_clk.o
obj-y += $(PROJECT_PATH)/camera_hw/

# Explicitly Include the Project Folder to catch any leftover configs
obj-y += $(PROJECT_PATH)/
