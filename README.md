# hecate
Hecate is designed to improve the security of Ubuntu 14/16 systems.

Note that auth should be run before perms, as auth creates a dependency
file for perms.

### update ###
Enables Ubuntu firewall, installs htop, and updates apt configuration to enable
auto updates and periodic update checks.
Update and upgrade the software packages currently installed on the system.

Note: A reboot is recommended after the system update process finishes.

### set_pass ###
Replaces all existing users passwords (except root password) with a
user-defined password. 
The max password age, minimum days between password change, and warn before
password change options are also set as follows:
- Max Password Age = 30 days
- Warn Before Password Change = 7 days
- Minimum days between password change = 0 days (can change any time)

### auth ###
Running auth removes any unauthorized users present on the system. If a user
isn't included in the user-defined file users.authorized, it will be removed
from the system. Including administrators is important! The users will be manually
entered at run-time.

A log of deleted users is stored in users.deleted.

### guest ###
Disabes the guest account on LightDM. Does not work on Ubuntu versions past
16.04 LTS.

### logindefs ###
Assigns PASS_MIN_DAYS, PASS_MAX_DAYS, and PASS_WARN_AGE to 0, 30, and 7, respectively.
It is not necessary to run this script after running set_pass.

### perms ###
Note: auth must be run before this script as auth creates users.authorized.
Alternatively, you can create and populate users.authorized if you do not want
to run auth.

This script manages users in the group sudo. If a user should be a member of sudo
(with respect to the user-defined file admins) then it will add them to the group
if they are not already a member. Otherwise, it will delete them from the group
sudo if they are a member and should not be.

### info (directory) ###
Required by update script. Contains update.template. See update section for more info.



