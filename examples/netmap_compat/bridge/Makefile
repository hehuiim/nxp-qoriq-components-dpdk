# SPDX-License-Identifier: BSD-3-Clause
# Copyright(c) 2010-2014 Intel Corporation

ifeq ($(RTE_SDK),)
$(error "Please define the RTE_SDK environment variable")
endif

# Default target, can be overridden by command line or environment
RTE_TARGET ?= x86_64-native-linuxapp-gcc

include $(RTE_SDK)/mk/rte.vars.mk

ifneq ($(CONFIG_RTE_EXEC_ENV_LINUXAPP),y)
$(info This application can only operate in a linuxapp environment, \
please change the definition of the RTE_TARGET environment variable)
all:
clean:
else

# binary name
APP = bridge

# for compat_netmap.c
VPATH := $(SRCDIR)/../lib

# all source are stored in SRCS-y
SRCS-y := bridge.c
SRCS-y += compat_netmap.c

CFLAGS += -O3 -I$(SRCDIR)/../lib -I$(SRCDIR)/../netmap
CFLAGS += $(WERROR_FLAGS)

include $(RTE_SDK)/mk/rte.extapp.mk

endif
