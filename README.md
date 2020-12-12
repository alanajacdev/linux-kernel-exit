# Linux-Kernel-Projects



# Basic Hello-World Kernel Module: 

Create Root Folder

```
mkdir ~/src/lkm_example
cd ~/src/lkm_example
```

Create Module from C file
```
#include <linux/init.h>
#include <linux/module.h>
#include <linux/kernel.h>MODULE_LICENSE(“GPL”);
MODULE_AUTHOR(“Robert W. Oliver II”);
MODULE_DESCRIPTION(“A simple example Linux module.”);
MODULE_VERSION(“0.01”);static int __init lkm_example_init(void) {
 printk(KERN_INFO “Hello, World!\n”);
 return 0;
}static void __exit lkm_example_exit(void) {
 printk(KERN_INFO “Goodbye, World!\n”);
}module_init(lkm_example_init);
module_exit(lkm_example_exit);
```


Create Makefile 
```
obj-m += lkm_example.oall:
 make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modulesclean:
 make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

Insert Compiled Kernel Module 
```
sudo insmod lkm_example.ko
```

Remove Running Kernel Module 
```
sudo rmmod lkm_example
```
