# RHEL 7.x artifacts for ImageStreamer v5.2 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v5.2 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
- The following RHEL versions are supported
  - RHEL 7.2
  - RHEL 7.3
  - RHEL 7.4
  - RHEL 7.6
  - RHEL 7.7
  
## EFI based artifacts

With the EFI based artifacts, ImageStreamer can support all the filesystems including XFS/BTRFS for RHEL Operating system.
This was not possible earlier because, Guestfish, used to customize the boot volume of the operating system, did not support XFS/BTRFS. 

Until now the root partition was mounted in the plan scripts, but now, to enable deployment using FAT32,  mount the partition (/boot/efi) and run the plan scripts through it for personalization, which provides support for all the filesystems.

## Version history
- HPE-RHEL7-EFI-2020-04-08-v5.2.zip 
	- supports both init and systemd boot process

# Prerequisite for using EFI Based Artifact bundle

## Note: 
- Please make sure you change Filesystem Attribute in the Server Profile creation page to desired filesystem type "only when you have a external drive attached to the blade"
- If you do not have a external hard drive attached to the blade please leave the default "disabled" option of filesystem attribute as is.
- LVM should be created at the time of installing the OS, on the bare metal, before image capture is done. The Filesystem type attribute in the Server Profile Page will not create LVM on the golden image which gets mounted, at the time of deployment.


## Golden Image creation for EFI based deployment of RHEL 7:

1.	Ensure that you have access to RHEL 7 ISO installation file containing iSCSI device drivers.

2.	Create a server profile with “HPE - Foundation 1.0 - create empty OS Volume” as OS Deployment plan and any available server 		hardware. Set an appropriate value for volume size in MiB units. The HPE Synergy Server will be configured for access to this 		empty OS Volume.

3.	Launch iLO Integrated Remote Console of this server and set RHEL 7 ISO file as virtual CD-ROM/DVD image file. Power on the 		server.

4.	When the Grub Screen appears edit the install linux line by pressing 'e' and add ip=ibft or rd.iscsi.ibft=1 to the end of the 		line which starts with 'kernel'

5.	RHEL installation starts and RHEL installer detects the configured empty OS Volume as an iSCSI disk device. Select this iSCSI 		disk device as the target for RHEL installation.

6.	Follow onscreen instructions and complete the RHEL installation.

7.	After the OS boots up Create the following directories.

      -	mkdir -p /boot/efi/EFI/HPE/isdeploy
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy/{scripts,tmp,data}

8.	Modify /etc/rc.d/rc.local. Add below line

      -	sh /boot/efi/EFI/HPE/isdeploy/HPE-ImageStreamer.bash
     
9.	Change permission of the rc.local file. (chmod 755 /etc/rc.d/rc.local)

10.	Edit /boot/efi/EFI/redhat/grub.cfg and change the hardcoded IP and MAC to ip=ibft (  ## Note: Make this change only if using 		either of the following setups - HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module )

11.	Power off the server. 

12.	Navigate to HPE Synergy Image Streamer -> Golden Images and Click ‘Create Golden image’ 
 
13.	Select the OS volume corresponding to the server profile created for empty OS volume and choose “HPE - Foundation 1.0 - capture 	OS Volume as is” as the capture build plan. 
 
14.	HPE Synergy Image Streamer captures RHEL image and adds it as a golden image.



## Follow the below document to load driver for HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module and Golden image capture process.

- https://github.com/HewlettPackard/image-streamer-rhel/blob/v5.2/docs/HPE%20Synergy%20ImageStreamer%20Documentation%20for%20RHEL%207.6%20for%20loading%20drivers%20during%20installation%20and%20Golden%20Image%20capture.pdf

## Artifact Bundle Contents:
--------------------------------------------------------------------------------

	            File name: HPE-RHEL7-EFI-2020-04-08-v5.2.zip
		Name (in manifest): HPE-RHEL7-EFI-2020-04-08-v5.2
		       Description: ImageStreamer artifacts for RHEL7 personalization and generalization.(c) Copyright 2019-2020 Hewlett Packard Enterprise Development LP. Licensed under the Apache License, Version 2.0 (the \"License\")...
		             Dated: 2020-04-08 (18:50:36)

--------------------------------------------------------------------------------

Build Plans:

	       Name: HPE-RHEL7-EFI-personalize-and-configure-NICs-LVM-2019-06-11 (Type:deploy)
	Description: Personalizes RHEL7 for XFS Partition using EFI and configures Multi NIC's  Copyright 2018 -2019 Hewlett Packard Enterprise Development LP Licensed under the Apache License, Version 2.0 (the "License");...


	       Name: HPE-RHEL7-EFI-personalize-and-configure-NIC-teamings-LVM-2020-04-08 (Type:deploy)
	Description: Personalizes RHEL7 for XFS Partition using EFI and configures NIC teaming (c) Copyright 2018-2020 Hewlett Packard Enterprise Development LP Licensed under the Apache License, Version 2.0 (the "License");...



Plan Scripts:

	       Name: HPE-RHEL7-EFI-configure-deployment-NIC-teaming-2020-04-06 (deploy)
	   FullName: 24e3db30-983e-49c7-bdb1-3f33932c4808_planscript.json
	Description: Script to configure deployment interface teaming (ibftNIC teaming)


	       Name: HPE-RHEL7-EFI-unmount-2019-03-21 (general)
	   FullName: 46795bfa-5021-43fa-ad4a-f798d1054b0c_planscript.json
	Description: Unmounts the EFI partition


	       Name: HPE-RHEL7-EFI-configure-management-NIC-teaming-2020-04-08 (deploy)
	   FullName: 5118a8a3-e6f5-4525-abf5-14a43a630b0a_planscript.json
	Description: Configures management NIC teaming.


	       Name: HPE-RHEL7-EFI-configure-hostname-2019-03-21 (deploy)
	   FullName: 5f4548d6-627b-49fc-8140-0b8e4f23b91e_planscript.json
	Description: Configure hostname


	       Name: HPE-RHEL7-EFI-configure-partition-using-LVM-2019-05-01 (deploy)
	   FullName: 72d49037-64d9-4078-9720-7cfc944b256a_planscript.json
	Description: LVM configuration using /boot/efi


	       Name: HPE-RHEL7-EFI-configure-multiple-NICs-2019-03-21 (deploy)
	   FullName: 799368cb-b4ea-4dfb-a3ca-2b7b0199aec9_planscript.json
	Description: Configures NICs


	       Name: HPE-RHEL7-EFI-mount-2019-03-21 (general)
	   FullName: a9cfe338-d8b6-48ef-8d98-b3cd28fb9abb_planscript.json
	Description: Mounts EFI partition (/dev/sda1) as root(/)


	       Name: HPE-RHEL7-EFI-configure-users-2019-03-21 (deploy)
	   FullName: c1a51f22-df0e-46f6-bd8e-d7443d2b9ad4_planscript.json
	Description: Sets root password and create user accounts


	       Name: HPE-RHEL7-EFI-manage-security-services-2019-03-21 (deploy)
	   FullName: c413c855-4e18-447e-9510-1e5f16978cc9_planscript.json
	Description: Enables/Disables SSH and Enables Selinux Security


	       Name: HPE-RHEL7-EFI-wrapper-2019-03-21 (deploy)
	   FullName: f31bc2ce-8c13-45cc-a281-41a8d9c39dac_planscript.json
	Description: This is a wrapper script where all other scripts are evoked.

