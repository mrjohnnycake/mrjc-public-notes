---
title: Locked Down Parental Controls for Children's Cellphones
---
# About this Guide

- This is for Android devices. I have tested and used this for my own child with a Google Pixel phone and can recommend that line
- 

> [!NOTE] A heads up for going forward with MDM
> - Sometimes the website will say you only have a set amount of time for your account before you need to upgrade. This is just marketing and can be ignored.
 > - The website is very techie and this process is not the most intuitive (and I say this as a computer nerd). Just hang in there and do each step and it should work just fine.
> - When you go to a menu item you haven't set up yet the website will often show a box with some boxes with options inside of it and some orange arrows pointing to different boxes. Just close this box and ignore.


# Setup Process Steps

1. Sign up for a free account:
	- Go [here](https://www.manageengine.com/mobile-device-management/free-trial.html?mdmfp_fmdms&cd) and create an account. You need to use your real email address but you can use whatever name and business name you'd like as there's no verification of those in the process. You do not need to enter your phone number.
	- Confirm your email
	- Choose a password
	- Your account should be complete. Be aware that I received an error after completing but I followed the "return to home" link (or whatever it was called) and everything was fine and ready to go

2. Add your child as a User:
	- Go to Enrollment --> Enroll --> Users
	- Click Add Users and then Single User
	- Enter your child's email (needs to be real and accessible)
	- Change the User Name if you wish
	- Click Add User

3. Create a Group
	- Go to Device Mgmt --> Manage --> Groups & Devices
	- Under the Groups tab, click Create Group then Device Group
	- Enter a name
	- Under Type choose Static
	- Click Create Group
		- I chose to call mine `lockeddown` as every device added to this group would have the most restrictions on them. This is helpful if you'll have multiple users and devices and will help track which devices belong to which settings.
	- Click OK on the empty group warning

4. Device
	- Go to Enrollment --> Enroll --> Devices
	- Under the Managed tab, click Android
	- Expand "Enrollment Methods for Company-Owned Devices"
	- Click QR Code Enrollment
	- Follow the instructions for Step 1 under 9.0 and later
	- On the device sign into a WiFi network
	- Follow the prompts on the phone and agree to the initial "this is a company controlled device" type stuff
	- On the Google Services screen you can choose what you would like turned off or on based on your own preferences though I suggest you at least keep Use Location turned on in this case
	- After the process is complete you will see that it still looks like a normal Android phone setup because it pretty much still is. The difference is that we get to control what stays on the phone or gets added in the coming steps.
	- Back on your computer, refresh the page and still on Enrollment --> Enroll --> Devices click on Assign User in the Action column of the device
		- Select your child's "user"
		- Under Assign to Group choose the group you created earlier
		- Under Device Name you can call it whatever you want (ie. My Kid's Phone)
		- Click Save or Okay or whatever it says

5. Setup a Managed Google Play Store
	- Go to Device Mgmt --> Manage --> App Repository --> Managed Google Play
	- Choose the "Google account" option
	- Click Configure Now
	- Enter your email and click next (ignore the warning)
	- Click Sign Up under Sign Up for Android Only
	- Click Get Started
	- Enter a Business Name (can be anything as this is not verified) and click Next
	- Put your own info in the Contact Details boxes then check the agreement box and click Confirm
	- Click Complete Registration

6. Create a Profile
	- Go to Device Mgmt --> Manage --> Profiles
	- Click Android
	- Give it a name
	- Choose MDM Profile
	- Click Continue
	- All of the changes I made were under Restrictions as that seemed to work for our situation (I didn't need Web Content Filters for instance because I blocked the Chrome browser altogether). You can adjust other categories at you own discretion. If a subcategory is not referenced here it is because I left it on the default settings
		- Security
			- Allow Adding or Removing Accounts on the Device: `Restrict All Accounts`
			- Restore Factory Settings: `Restrict`
			- Safe Mode: `Restrict`
			- Developer Mode: `Restrict`
			- Google Play Protect: `User Controlled` (I think I changed this due to a specific app's needs)
		- Applications
			- Users can install only approved apps: `Yes`
			- Allow installing non-market apps: `No`
			- Allow uninstalling apps: `No`
			- Stop system apps: `No`
		- Network and Roaming
			- Allow users to configure VPN: `No`
		- Location settings
			- Location services: `Always On`
	- Click Save
	- Click Publish
	- On the top of the page click on "here" to Associate Profile to Groups/Devices
		- This brings you to Device Mgmt --> Manage --> Groups & Devices --> Groups in case they've changed something and you don't see "here"
	- Click the checkbox on the Group you made earlier
	- Click Action and select Associate Profile
	- Select the Profile you just created and click Associate

7. On the Phone
	- When you clicked Publish in the last step the website sent the new settings we now require to the phone. If you look at the phone you will see that you will need to setup a screen lock in the next 60 minutes or be locked out of the device. If you child is not around you can create your own and they can change it later.
	- You need to sign in to your child's account on the phone for some of this stuff, like installing apps, to work. Go into Android settings and add your child's Google account as you usually would.

8. Apps
	- The phone comes with some apps preinstalled. You can limit or disable (blacklist) those apps if you wish.
	- You can also add apps from the App Store
	- You can manage apps in two different places (listed below) but adding apps is easier in the App Repository option as it's easier to find the apps
		- Device Mgmt --> Manage --> App Repository
		- Inventory --> Inventory --> Apps
	- Some apps are required by the system and should not be disabled. If I haven't disabled a system installed app it's probably because I tried to and it broke something so start out with my suggestions and make changes later as you get more comfortable with the process.
		- Chrome is the notable exception because it has to be installed to be able to set up some things and apps. Since I don't want my child to have a browser on his phone I got around this by allowing Chrome during the phone system and app setup processes and then after the phone and apps were working properly I blacklisted (disabled) Chrome. It has not been an issue but be aware that if you install a new app later down the line that you may need to re-enable Chrome to setup the app and get it functioning and afterwards you can then re-disable it.

9. Adding Play Store Apps
	- Go to Device Mgmt --> Manage --> App Repository and stay on the Apps tab
	- Click on Add App and select Play Store App
	- Search for an app (ex. Google Docs), click the app, click Select, and click Save & Sync
	- Click Sync again if asked
	- In my experience I had to refresh the page for the app to show up in the table
	- After you've added the app click on it in the table (refresh the page if it doesn't show up)
	- Click Distribute
	- Select the Group you made earlier
	- Choose Silent Installation
	- Click Distribute App
	- The app will download to the phone

10. Blacklisting Apps
	- Even if the app is preinstalled you still need to add the app just you did in the last step
	- After you've added the app click on it in the table (refresh the page if it doesn't show up)
	- Click Distribute
	- Select the Group you made earlier
	- Choose Distribute to app catalog
	- Click Distribute App
	- Now go to Inventory --> Inventory --> Apps
	- Check the box next to the app you want to blacklist (they call it blocklist)
	- Click on Blocklist App and Specific groups/devices
	- Select your group and click Blocklist
	- The app will disappear from the phone
