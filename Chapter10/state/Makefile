obj-m := state.o
ifeq ($(RELEASE),1)
	BUILD = release
else
	BUILD = debug
endif

ifeq ($(TARGET),armv7l-linux-kernel-module)
state-objs := target/$(TARGET)/$(BUILD)/libstate.a
else
state-objs := target/x86_64-linux-kernel-module/$(BUILD)/libstate.a
endif
EXTRA_LDFLAGS += --entry=init_module

ifeq ($(TARGET),armv7l-linux-kernel-module)
CMD_LINE = ARCH=arm CROSS_COMPILE=$(CROSS)
else
KDIR = /lib/modules/$(shell uname -r)/build
CMD_LINE =
endif

all:
	$(MAKE) $(CMD_LINE) -C $(KDIR) M=$(CURDIR)

clean:
	$(MAKE) -C $(KDIR) M=$(CURDIR) clean
