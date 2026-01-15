---
title: Locked Down Parental Controls for Children's Cellphones
---
After dealing with the existing parental controls available on the market for our firstborn's cellphone I found the options very lacking. Most of the products had one or more of these problems:

- Overpriced monthly fees
- Inability to choose your own service carrier
- Required frequent approving of this or that on behalf of the child
- A tech-savvy kid could figure out how to break the parental controls
- Child's account ages out of parental controls too early / young

I wasn't happy with the solution we chose but after a while it felt too late to switch it up and I wasn't even sure what I would change.

When the time came for our other child to get a phone I went to the pros: IT nerds. They all said the same thing and that was to use MDM. I didn't even know what that was.

Long story short, MDM is the technology that larger businesses use to manage the phones and computers of their employees. There's a ton you can do with it. If you want to give someone a fully functioning phone that you just want to keep location tabs on you can do it. If you want to give someone a smartphone that can only make and receive phone calls you can do that.

However, although the potential was there I found it's easier said than done and a lot of options are cost prohibitive as well. I ended up finding a popular service called ManageEngine MDM and after a lot of hair pulling I got it working and am very happy with it. The best part is that it's also free.

Recently my kid accidentally broke their phone so I had to redo the MDM and realized I'd quickly forgotten how to set it up. So to save me time in the future, and to help other parents looking for a good solution, I set it up again and documented the process step by step.

Hope this helps you.

# About this Guide

- This guide is written for Android devices because that's what I prefer. I have tested and used this for my own child with an Android-based Google Pixel phone and I can recommend that line.
- If you have a different Android phone this guide should still work fine but the website has a couple warnings about Samsung phones. They'll still work but there are some considerations you'll have to understand.
- This guide DOES NOT cover setting up an iPhone BUT the basic premise / line-of-thinking should be the same. I'd suggest just thinking each step thru and you'll probably figure out what to do differently.
- I've made this guide to help you figure it out for yourself. If I know you personally you can ask me for pointers AFTER you've set it up. I have considered setting it up for a fee though so I'll think about that.
- I'm very happy with the result. It'll probably take an hour but I think it's worth it.

# What this Guide DOESN'T Cover

- I don't use traditional parental controls like content filtering with this service simply because my configuration is locked down in a way that they wouldn't do much. A lot of that is due to the fact that there's no browser on my kids phone. If you want to include a browser I'd suggest setting up something like Google's Family Link after this guide.
- At the end of the day nothing can stop your child from taking about some nefarious stuff on the phone or sending messages with content you wouldn't approve of to their friends or even a stranger. To stop that with technology is an arduous task and I would suggest it's a losing battle. Instead I choose to keep an open dialogue with my kids and raise them to make good choices for themselves in hopes that when they are alone with their phone that they'll make better choices. MDM or any other parental controls will never match being a good parent and/or member of society.

# Setup Process Steps

> [!NOTE] A heads up for going forward with ManageEngine MDM
> - This process is not for the faint of heart. However, this guide should take almost all of the guessing out of it so I think most people can follow along just fine.
> - Sometimes the website will say you only have a set amount of time for your account before you need to upgrade and pay. This is just marketing and can be ignored and you'll be fine with the free plan.
> - When you go to a menu item that you haven't set up yet the website will often show a box with smaller boxes inside that have options and some orange arrows pointing to these different boxes. Just close this box and ignore.

1. Sign up for a free account:
	- Go [here](https://www.manageengine.com/mobile-device-management/free-trial.html?mdmfp_fmdms&cd) and create an account. You need to use your real email address but you can use whatever name and business name you'd like as there's no verification of those in the process. You do not need to enter your phone number.
	- Confirm your email
	- Choose a password
	- Your account should be complete. Be aware that I received an error after completing the account creation process but I followed the "return to home" link (or whatever it was called) and everything was fine and ready to go.

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
