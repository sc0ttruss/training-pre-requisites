# training-pre-requisites

Workstation install pre-requisites for chef training, using chefdk, vagrant and testkitchen

# Chef training.  Requirements for class 

Staying current with the lastest versions is the way of Devops.
Bring your own Laptop required, no equipment will be provided.
Only the workstation setup sections are mandatory pre-requisites for course attendance.

Windows workstation setup with chefdk/testkitchen ( 15 minutes approx. )
Linux workstation setup with chefdk/testkitchen ( 15 minutes approx. )
Additional Resources
Recommended editors for text editing
Generate a windows virtualbox windows image.
Chef Fundamentals Checklist - Classroom requirements


# Windows workstation setup with chefdk/testkitchen ( 15 minutes approx. )

At least 15Gb free space, needed for vm images. 
install:-
chefdk, -  https://downloads.chef.io/chef-dk 
virutalbox  - https://www.virtualbox.org/wiki/Downloads
vagrant - https://www.vagrantup.com/downloads.html
git - use github install https://windows.github.com/
Path problems  - On Microsoft Windows, C:/opscode/chefdk/bin must be before C:/opscode/chefdk/embedded/bin in the PATH.

Run the following commands to verify the install, if not working, fix. 
```
chef -v
chef verify 
vagrant plugin install virtualbox
vagrant plugin install vagrant-winrm
```
note replace <username> with your windows username
```
cd c:\users\<username>\
mkdir Source
cd Source
kitchen init
```
Edit “.kitchen.yml” file in current directory ( ensure you have the full stop at the beginning of the file name ), and change the  following :-
Change from this:-
```
  platforms:
    - name: ubuntu-12.04
    - name: centos-6.4
```
To this:-
```
  platforms:
    -	name: centos-7.1
```
Now run the following:-
```
kitchen list
```
This command also validates the yaml file format in '.kitchen.yml' file, so get used to running this after every edit of the file
```
kitchen create
kitchen diagnose
kitchen destroy 
```
note: this destroys the machine, you might want to do a kitchen login to play around before destruction
nb  ssh.exe is needed, and should use a 'git shell' from the github install above.  There are other alternatives to using 'git shell', but this will not be covered as part of the course.
Troubleshooting, ensure no spaces in the path on local directory
If you find, the centos box and linux troublesome, then you can generate your own virtualbox image and use winrm to connect instead of ssh, but beware, this is a lot more involved.  Instructions follow at the end of this document, with title 'Generate a windows virtualbox windows image'. 

Install a better shell in windows - Conemu is a better shell for windows development 
http://conemu.github.io/


# Linux workstation setup with chefdk/testkitchen ( 15 minutes approx. )

At least 15Gb free space, needed for vm images. 
install:-
chefdk, -  https://downloads.chef.io/chef-dk 
virutalbox  - https://www.virtualbox.org/wiki/Downloads
vagrant - https://www.vagrantup.com/downloads.html
# Linux - Ubuntu specific - workaround
```
echo 'export PATH="/opt/chefdk/embedded/bin:$PATH"' >> ~/.bash_profile && source ~/.bash_profile
```
go to ~/.bashrc and add the following entry towards the end of file
```
#Source bash_profile to set JAVA_HOME and add it to the PATH because for some reason is not being picked up 
. ~/.bash_profile
#To avoid ssl errors when downloading with man in the middle proxy for ssl.
Create or modify a file called .gemrc in your home path, including the line :ssl_verify_mode: 0
```
End of Ubuntu specific workaround

Run the following commands to verify the install, if not working, fix. 
```
chef -v
chef verify
vagrant plugin install virtualbox
vagrant plugin install vagrant-winrm 
cd ~
mkdir Source
cd Source
kitchen init
```
Edit “.kitchen.yml” file in current directory ( ensure you have the full stop at the beginning of the file name ), and change the  following :-
```
Change from this:-
  platforms:
    - name: ubuntu-12.04
    - name: centos-6.4
```
To this:-
```
  platforms:
    -	name: centos-7.1
```
Now run the following:-
```
kitchen list
```
This command also validates the yaml file format in '.kitchen.yml' file, so get used to running this after every edit of the file
```
kitchen create
kitchen diagnose 
kitchen destroy
```
note: this destroys the machine, you might want to do a 'kitchen login' to play around before destruction.

#   End of workstation setup/config, the remainder of this document is for informational and reference purposes, however it you are interested, read on.


# Additional Resources

http://www.chef.io

http://learn.chef.io

http://docs.chef.io

Email info@chef.io

Twitter @Chef

Install Chef
http://chef.io/chef/install

Chef Cookbooks
http://supermarket.chef.io

Chefdk - Chef Development Kit
https://downloads.chef.io/chef-dk/

YouTube
http://youtube.com/getchef

Community Site
http://supermarket.chef.io

Freenode IRC
 #chef, #chef-hacking, #openstack-chef

Chef mailing lists - just normal chef is best for cookbooks ( chef@lists.opscode.com )
http://lists.opscode.com/sympa/info/chef - click the subscribe on the left hand side of page
Full list is here https://docs.chef.io/community_lists.html
              
Chef Bento images and packer
https://github.com/chef/bento

Testkitchen providers, good reference for connecting to clouds with kitchen
http://misheska.com/blog/2014/09/21/survey-of-test-kitchen-providers/

hyperV with Testkitchen
http://www.hurryupandwait.io/blog/orchestrating-multi-server-tests-in-test-kitchen

Create hyper-V windows VM
http://www.hurryupandwait.io/blog/in-search-of-a-light-weight-windows-vagrant-box

Chef-provisioning with Azure
http://stuartpreston.net/2015/02/chef-provisioning-with-microsoft-azure-part-1/

Analytics splunk app
https://splunkbase.splunk.com/app/2687/

Good list of Ohai plugins https://github.com/rackerlabs/ohai-plugins/tree/master/plugins

PKI - How to control multiple private keys in chef
https://github.com/opscode-cookbooks/chef-vault

kitchen-hyperv
https://github.com/test-kitchen/kitchen-hyperv


Security related
Chef Audit Mode: CIS Benchmarks
https://www.chef.io/blog/2015/04/09/chef-audit-mode-cis-benchmarks

Audit mode of chef client – Security related
http://infra-talk.org/author/joshua-timberman

Chef server default ports
https://docs.chef.io/server_firewalls_and_ports.html

Random
Multinode test kitchen
http://www.hurryupandwait.io/blog/orchestrating-multi-server-tests-in-test-kitchen

Build images for azure
https://github.com/MSOpenTech/packer-azure

Introduction to Testing with Chef
Videos 
https://www.youtube.com/playlist?list=PL11cZfNdwNyMp0BXY_nCOZ4odCqofq6oA

Code
https://github.com/chef-training/introduction_to_testing

# Recommended editors for text editing.  Not mandatory, any text editor will do, but some are more efficient.
Sublime text 

Sublime text links:- 

http://www.bonusbits.com/main/HowTo:Install_Chef_Support_in_Sublime_Text

sublimetext chef plugin helper.

http://www.bonusbits.com/main/HowTo:Install_Chef_Support_in_Sublime_Text

Sublime text plugin for a shell “sublimeREPL” and the fixes required to get it working

Here are the links, describing fix for PRY: 

description: 
http://vikingcodingadventures.tumblr.com/post/97746105649/setting-up-sublimerepls-pry-ruby-cli-in-sublime

fix: 
https://github.com/wuub/SublimeREPL/pull/372/files



# Generate a windows virtualbox windows image. 
Install:
Packer   https://packer.io/
Path problems  - On Microsoft Windows, C:/<PATHTOPACKER> must be in the PATH.
Hint:  change <PATHTOPACKER> to the place where packer.exe is installed
```
cd c:\users\<username>\Source
git clone https://github.com/boxcutter/windows.git
cd windows
make virtualbox/eval-win2012r2-standard nocm
```
note: this installs with "no config management - nocm", also this downloads the “.ISO” image for windows2012r2, so, beware of bandwidth issues.

Note, packer relies on 'make', and unless you have this configured and working ( eg you have installed Microsoft Virtual Studio ).  Configuration and installation of make is beyond the scope of this class.   The alternative, is to install packer on a linux workstation ( make comes by default ), and build the images there. ( this is almost an anti-pattern, but it is so much easier on linux to build a windows image ).

# Chef Fundamentals Checklist - Classroom requirements

 - How many people will join the training and what's their background?
eg, developer, sysadmin, manager etc.

 - What operating systems are being used for workstations/laptops?
Admin access required for windows, usb ports working ( please advise if this is against security policy ).

 - What operating systems are planned to be managed by Chef?
Primary OS, secondary OS etc...

Admin rights needed for laptops ( normally windows ), needs to be verified and working before the class!  Otherwise the pre-requisites have not been met. 


## Classroom requirements

Strong wifi, 2.4Ghz/5Ghz preferred, wifi username/password

If you are providing a classroom, it should be large enough to accommodate the entire class comfortably, with a table and chair for each person.  

Internet access is required in the classroom, wifi is OK, but it has to work, as internet access is a mandatory part of the class.  ( vm cloud instance will be provided for each student )

Projector and screen with vga/hdmi/DVI cable

Power sockets for all students, near to their desks ( power bars are ok. )

Whiteboard, or flip chart with pens and eraser ( whiteboard )

Ready supply of bottled water/access to refreshments

Preferably place to obtain coffee/tea at break time.  

On site lunch/snacks if possible



