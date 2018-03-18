# Arch Linux Post Installation Setup and Config Scripts

This README contains the steps I do to configure and set up a new Arch Linux installation running XFCE Desktop and all my preferred applications. The shell scripts in this repo allow the entire process to be automated. I also run some personal scripts that configure my dotfiles and various other things. Those are not available publicly. I'm posting this publicly in case it might be useful to someone.

### Don't just run these scripts. Examine and customize them for your needs.


## Description
I run XFCE desktop since it's fast and lightweight. I don't install a greeter, preferring to always boot into the terminal by default. That way, if there is ever a show-stopping problem with the GUI I can fix it without having to bood from an external drive.

I also install the LTS Kernel along side the rolling one and configure my bootloader to offer both as a choice during startup. This enables me to switch kernels in the event of a problem with a new version.

I run my own utilites: __[WifiVPN](https://github.com/rickellis/WifiVPN)__ for network connectivity, and __[AURIC](https://github.com/rickellis/AURIC)__ for AUR package management.

The install steps are as follows:

### Install Arch Linux

Follow the steps in my __[Arch Linux Installation Gude](https://github.com/rickellis/Arch-Linux-Install-Guide)__. Then:

---

### Boot into new installation

    $   sudo wifi-menu

---

### Install Reflector. 

First update the pacman databases:

    $   sudo pacman -Sy

    $   sudo pacman -S reflector rsync curl

Now generate mirrorlist:

    $   reflector --verbose --country 'United States' -l 5 --sort rate --save /etc/pacman.d/mirrorlist

---

### Initialize .gitconfig file

    git config --global user.name "rickellis"
    git config --global user.email "rickellis@gmail.com"

---

### Clone Archomatic
These are the scripts in this repo.

    $   git clone https://github.com/rickellis/Archomatic.git

---

### Run Archomatic files

Run the following scripts:

    $   ./1-xorg.sh
    $   ./2-xfce.sh 
    $   ./3-network.sh 
    $   ./4-bluetooth.sh 
    $   ./5-audio.sh 
    $   ./6-printers.sh 
    $   ./7-software-pacman.sh
    $   ./8-software-aur.sh
    $   ./9-setup.sh

### Reboot

    $   reboot

### Initialize Xorg:
At the terminal, run:

    $   xinit

If it doesn't automatically boot into XFCE run:

    $   startx


You should now have an Arch system running XFCE.

Congrats!