# VirtualHere Reverse USB Customer Module for Linux

On Windows, USB Redirector Technician Edition is commonly used by smartphone repair industry, so the repair man does not need to install the proprietary smartphone flash tool to customer.
But what if the customer only has Linux machine and unwilling to install Windows for many reason?
VirtualHere USB Server for Linux can do the job.

## Usage

1. The technician need to [install VirtualHere USB Client from here](https://www.virtualhere.com/usb_client_software), enable Reverse Client feature, and ensure the port 7573 open to public. If the technician does not have a public IP address, We strongly recommend you to purchase EasyFind Subscription, or install your flash tool and VirtualHere USB Client on a Windows VPS instead.
2. Assuming your public IP address is resolved from `yourdomain.example.com`. Ask the customer to execute this command and enter the sudo password when prompted. 
```
curl https://raw.githubusercontent.com/HikariCalyx/virtualhere_usb_redirector_linux/main/virtualhere_reverse | sudo bash -s - yourdomain.example.com:7573
```
However if the domain parameter is not given, you'll be asked to input the domain yourself:
```
curl https://raw.githubusercontent.com/HikariCalyx/virtualhere_usb_redirector_linux/main/virtualhere_reverse | sudo bash
```
4. Now ask the customer to connect the device under proper mode (e.g. Fastboot for Android device) to Linux machine.

![Showcase.gif](https://github.com/HikariCalyx/virtualhere_usb_redirector_linux/assets/29157608/d131e640-934e-47db-9bc8-15d250d034a6)

5. The technician can now operate this device. To terminate the procedure, add a Reverse Client named ```stop.local```.

## Known issues
* If the customer's Linux machine already has VirtualHere USB Server running as service, it must be stopped first:
```
sudo systemctl stop virtualhere
```
* Break during Step 2 and 3 may not work reliably.

## Thoughts

Actually, VirtualHere Pty. Ltd could release a special edition of VirtualHere solely for this purpose.
