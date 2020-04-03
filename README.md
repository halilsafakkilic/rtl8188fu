For Kernel 4.15.x ~ 5.4.x (All Debian Derivatives)

------------------

## How to install

If you using a Raspbian;

`sudo apt-get install build-essential git dkms raspberrypi-kernel-headers`

Anything else

`sudo apt-get install build-essential git dkms linux-headers-$(uname -r)`

&nbsp;

*Clone Repository*

`git clone https://github.com/halilsafakkilic/rtl8188fu`

&nbsp;

**Important:**
If you using a Raspbian and if you get the "arch/armv7l/makefile no such file or directory" error of build; then remove module please using "sudo dkms remove rtl8812AU/4.3.14 --all" command. Now open *Makefile* then after replace "ARCH ?= $(SUBARCH)" to "ARCH ?= arm" and save. Now repeat the **Kernel Build** stages.

&nbsp;

*Kernel Build*

`sudo dkms add ./rtl8188fu`

`sudo dkms build rtl8188fu/1.0`

`sudo dkms install rtl8188fu/1.0`

`sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/`

*Note:* If you need a add your other linux driver module in a kernel please visit https://hardikpatelblogs.wordpress.com/2010/11/19/8/.

------------------

Run following commands for disable power management and plugging/replugging issues.

`sudo mkdir -p /etc/modprobe.d/`

`sudo touch /etc/modprobe.d/rtl8188fu.conf`

`echo "options rtl8188fu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8188fu.conf`

------------------

## How to uninstall

`sudo dkms remove rtl8188fu/1.0 --all`

`sudo rm -f /lib/firmware/rtlwifi/rtl8188fufw.bin`

`sudo rm -f /etc/modprobe.d/rtl8188fu.conf`


------------------

## How to install from PPA repository

You can install rtl81188fu driver with following commands from PPA. For current supported distros and package details, visit https://launchpad.net/~kelebek333.


`sudo add-apt-repository ppa:kelebek333/kablosuz`

`sudo apt-get update`

`sudo apt install rtl8188fu-dkms`


You can purge packages with following commands

`sudo apt purge rtl8188fu-dkms`
