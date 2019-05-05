KDIR ?= /lib/modules/$(shell uname -r)/build

all:
	make -C $(KDIR) M=$(PWD) src=$(PWD) modules

clean:
	make -C $(KDIR) M=$(PWD) src=$(PWD) clean
