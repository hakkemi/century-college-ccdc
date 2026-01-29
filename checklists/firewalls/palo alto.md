# Change Password
## CLI MODE

Enter configuration mode:
`configure`
Set the new password:
`set mgt-config users admin password`
Commit the change to save:
`commit`

## INTERFACE MODE

Log in to the Palo Alto web UI via [https://172.20.242.150/](https://172.20.242.150/)
Navigate to Device > Administrators. 
Select the admin account and click Edit.
Enter the new password and confirm. 
Click OK to save. GUI version

# RESET PASSWORD
Reboot the firewall. 
Press 'm' (or 'maint' on newer models) during boot. 
Select "Select Running Config" and load a previously saved config with known credentials. 
If no valid config exists, perform a factory reset (erases all settings)