# iron-man-eionix-plymouth-theme
This is a Plymouth theme.

[![Video](https://raw.githubusercontent.com/krishnan793/iron-man-eionix-plymouth-theme/master/preview.gif)](https://www.youtube.com/watch?v=c6f478VBhtE)


[Video] https://www.youtube.com/watch?v=c6f478VBhtE

[Blog] https://www.eionix.co.in/2016/10/30/plymouth-theme-for-ubuntu.html

# Installation

Clone this repository.

    sudo git clone https://github.com/krishnan793/iron-man-eionix-plymouth-theme.git /usr/share/plymouth/themes/iron-man-eionix-plymouth-theme

After installing you can test the theme through (as root, preferably on a tty):

    # plymouthd
    # plymouth --show-splash
    # plymouth --quit

## On most distros

(Tested on openSUSE Tumbleweed)

### Set GRUB2 up

Check `/etc/default/grub`. It should include the following:

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

* If there are other parameters defined in `GRUB_CMDLINE_LINUX_DEFAULT="..."` you don't have to remove them unless they conflict with the ones above.
* `quiet` and `splash` are required to start plymouth
* Additionally you might have to [enable KMS](https://unix.stackexchange.com/a/110589) e.g. in case you're using integrated graphics by Intel by adding `i915.modeset=1`.

Reconfigure GRUB2, if you had to add something:

    sudo grub2-mkconfig -o /boot/grub2/grub.cfg

### Activate the theme

Check that the theme ended up in the right place:

    sudo plymouth-set-default-theme --list

Set the theme as default:

    sudo plymouth-set-default-theme iron-man-eionix-plymouth-theme -R

The -R option rebuilds the initrd automatically which is necessary.

## On Ubuntu

Install the theme.

    sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/iron-man-eionix-plymouth-theme/iron-man-eionix-plymouth-theme.plymouth 100

Select the default theme.

    sudo update-alternatives --config default.plymouth

Update the initramfs image.

    sudo update-initramfs -u

Now reboot.

If you want to install this on < Ubuntu 16.04, change the path from /usr/share/plymouth to /lib/plymouth/ . You need to do this on the iron-man-eionix-plymouth-theme.plymouth file also.
