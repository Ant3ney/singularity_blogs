+++
date = '2025-12-06T21:05:32-08:00'
draft = false 
title = 'Anthonys Arch Setup'
+++

# Anthonys Arch Setup

## 1. Boot Into Arch and Run the Installer

1. Create an Arch USB using Etcher or Ventoy.
2. Boot the laptop from USB.
3. When the terminal loads, run:

```bash
archinstall
```

### Install Settings
Here is what I did for these settings. Some are abvious and I'm not trying to be condisending. Think of this section as a checklist

#### *Archinstall language*
Select_language = "English"

#### *Locales*
Keyboard_layout = "us"
Locale_language = 'en_US.UTF-8"
Locale encoding = UTF-8

#### *Mirrors and repositories*
Do nothing

#### *Disk configuration*
Select "Partitioning"
Then select "Use a best-effort default partition layout"
Select the main hard drive
Select the filesystem ext4. Select btrfs if you want better snapshot and rollback support but this type is less battletested.
It will ask if you want to make a seperate partition for /home. Chose no unless you know what your doing

#### *Swap*
Do nothing

#### *Bootloader*
Bootloader = "Grub"

#### *Kernels*
Do nothing

#### *Hostname*
Hostname = "anthopc" // name this whatevery you want your pc name to be

#### *Authentication*
Select "Root password"
Set the root passowrd
Select User account
Select Add a user
type a root password
Select "add new user"
Type a user name
type password for that user
Do nothing for U2F login setup


#### *Profile*
Select "Type"
Select "Desktop"
Select "KDE Plasma"

#### *Applications*
Select "Bluetooth"
Select "Yes"

#### *Network Configuration*

#### *Additional packages*

#### *Timezone*
Select "America/Los_Angeles"

#### *Automatic time sync (NTP)*
Select "Yes"

#### Save the configuration
Then press Install

### Misc
If it asks you to if you want to create a seperate partitoin for /home say no unless you know what your doing

Use X11 if it recomends it to you and your using a cheap toster computer

## Wifi
Go to System Settings
Select Connections
Press the Pluss Button.
You can use this menu to add Wifi Manualy if you don't see your network in this menu. It may be needed to do so manualy. Your on linux after all.
