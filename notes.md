
Trying to follow this blog post:
https://rkrishnan.org/posts/2013-10-25-plan9-on-qemu.html

Download ISO from here: http://9front.org/iso/

`apt-get install qemu qemu-user qemu-utils`

Run this:

```
$ qemu-system-x86_64 -hda 9front.qcow2.img -cdrom ./9front-8392.16c5ead832f2.amd64.iso -boot d -vga std -m 768
```

It will boot the system from the .iso image and allow to install into the disk
image. Run `inst/start` when that boots. Answer a lot of questions.

One of these two commands should allow booting that freshly installed system,
but they both fail to boot for some reason:

```
$ qemu-system-x86_64 -hda 9front.qcow2.img -boot c -vga std -m 768
$ qemu-system-x86_64 -vga std -m 768 -device virtio-scsi-pci,id=scsi -drive if=none,id=vd0,file=9front.qcow2.img -device scsi-hd,drive=vd0
```

Probably I messed something up with the installation options.

Another blog post, this one seems to be quite recent and useful:
https://danieljames.cc/plan9-on-qemu/

Installed vim: https://vmsplice.net/9vim.html
installation via contrib/install stefanha/vim got me a 386 binary, which doesn't
work. So I compiled the binary from source, as instructed in the link above.

