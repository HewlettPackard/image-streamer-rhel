# RHEL 7.x, 8.x and 9.x artifacts for ImageStreamer v6.40 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v6.40 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
- The following RHEL versions are supported
	- RHEL 7.2
	- RHEL 7.3
	- RHEL 7.4
	- RHEL 7.6
	- RHEL 7.7
	- RHEL 7.8
	- RHEL 8.3
	- RHEL 8.4
	- RHEL 8.5
	- RHEL 8.6
	- RHEL 9.0
  

## EFI based artifacts

With the EFI based artifacts, ImageStreamer can support all the filesystems including XFS/BTRFS for RHEL Operating system.
This was not possible earlier because, Guestfish, used to customize the boot volume of the operating system, did not support XFS/BTRFS. 

Until now the root partition was mounted in the plan scripts, but now, to enable deployment using FAT32,  mount the partition (/boot/efi) and run the plan scripts through it for personalization, which provides support for all the filesystems.

## Version history
- HPE-RHEL7-EFI-2020-04-08-v6.40.zip 
	- supports both init and systemd boot process
- HPE-RHEL8-EFI-2020-10-27-v6.40.zip 
	- supports only systemd boot process
	- added support for RHEL 9.0
	- There is a change in the capture procedure for RHEL 9. Details below.

## Known issue

known RHEL8.4 rdma-core related issue while installing OS ,it will fail to start rdma services. 
Issue will be applicable for all vendors, not related to specific adapters. 
After OS installation this service starts itself. Please check the status after OS installation as below: 

# systemctl status rdma-ndd.service
   rdma-ndd.service - RDMA Node Description Daemon
   Loaded: loaded (/usr/lib/systemd/system/rdma-ndd.service; static; vendor preset: disabled)
   Active: active (running) since Tue 2021-08-10 12:39:01 IST; 1 weeks 0 days ago
     Docs: man:rdma-ndd
Main PID: 2071 (rdma-ndd)
    Tasks: 1 (limit: 822332)
   Memory: 1.0M
   CGroup: /system.slice/rdma-ndd.service
           ââ2071 /usr/sbin/rdma-ndd --systemd

Aug 10 12:39:01 B3D730c systemd[1]: Starting RDMA Node Description Daemon...
Aug 10 12:39:01 B3D730c systemd[1]: Started RDMA Node Description Daemon

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


## Golden Image creation for EFI based deployment of RHEL 8:

1.	Ensure that you have access to RHEL 8 ISO installation file containing iSCSI device drivers.

2.	Create a server profile with “HPE - Foundation 1.0 - create empty OS Volume” as OS Deployment plan and any available server 		hardware. Set an appropriate value for volume size in MiB units. The HPE Synergy Server will be configured for access to this 		empty OS Volume.

3.	Launch iLO Integrated Remote Console of this server and set RHEL 8 ISO file as virtual CD-ROM/DVD image file. Power on the 		server.

4.	When the Grub Screen appears edit the install linux line by pressing 'e' and add ip=ibft or rd.iscsi.ibft=1 to the end of the 		line which starts with 'kernel'

5.	RHEL installation starts and RHEL installer detects the configured empty OS Volume as an iSCSI disk device. Select this iSCSI 		disk device as the target for RHEL installation.

6.	Follow onscreen instructions and complete the RHEL installation.

7.	After the OS boots up Create the following directories.

      -	mkdir -p /boot/efi/EFI/HPE/isdeploy
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy/{scripts,tmp,data}
            
 8.	As RedHat has deprecated init boot up process the method of running scripts through local.sh will not work with RHEL8
 
 9.	To make personalization work a systemd process needs to be created which will call the wrapper script. Please fallow below steps 	 for creating a systemd process 
  
       - cd /etc/systemd/system/
       - vi personalization.service (add Below line in this file save and exit)
	
		[Unit]
		Description=Personalization
		After=network-online.target

		[Service]
		Type=oneshot
		RemainAfterExit=yes
		WorkingDirectory=/boot/efi/EFI/HPE/isdeploy/
		ExecStart=/bin/bash HPE-ImageStreamer.bash

		[Install]
		WantedBy=multi-user.target

10.	Enable the service "systemctl enable personalization.service"

11.	Power off the server. 

12.	Navigate to HPE Synergy Image Streamer -> Golden Images and Click ‘Create Golden image’ 
 
13.	Select the OS volume corresponding to the server profile created for empty OS volume and choose “HPE - Foundation 1.0 - capture 	OS Volume as is” as the capture build plan. 
 
14.	HPE Synergy Image Streamer captures RHEL image and adds it as a golden image.

## Golden Image creation for EFI based deployment of RHEL 9:

1.	Ensure that you have access to RHEL 9 ISO installation file containing iSCSI device drivers.

2.	Create a server profile with “HPE - Foundation 1.0 - create empty OS Volume” as OS Deployment plan and any available server 		hardware. Set an appropriate value for volume size in MiB units. The HPE Synergy Server will be configured for access to this 		empty OS Volume.

3.	Launch iLO Integrated Remote Console of this server and set RHEL 9 ISO file as virtual CD-ROM/DVD image file. Power on the 		server.

4.	When the Grub Screen appears edit the install linux line by pressing 'e' and add ip=ibft rd.iscsi.firmware inst.nonibftiscsiboot 		to the end of the line which starts with 'kernel'

5.	RHEL installation starts and RHEL installer detect the configured empty OS Volume as an iSCSI disk device.
	
	**Note:**in RHEL9.0 "Installation Destination" may show error, open "Installation Destination" and Select the iSCSI disk device 		as the target for RHEL installation.

6.	Follow onscreen instructions and complete the RHEL installation.

7.	During first OS boot, press 'e' to edit the boot loader options and add ip=ibft rd.iscsi.firmware to the end of the line		 which starts with 'kernel'

8.	After the OS boots up 
	- Create the following directories.
		- mkdir -p /boot/efi/EFI/HPE/isdeploy
		- mkdir –p /boot/efi/EFI/HPE/isdeploy/{scripts,tmp,data}
	- execute the following command to set the boot loader options for ibft
		- grubby –update-kernel=/boot/vmlinuz-$(uname –r) –args="ip=ibft rd.iscsi.firmware"

9.	As RedHat has deprecated init boot up process the method of running scripts through local.sh will not work with RHEL9
 
10.	To make personalization work a systemd process needs to be created which will call the wrapper script. Please fallow below steps 	 for creating a systemd process 
  
       - cd /etc/systemd/system/
       - vi personalization.service (add Below line in this file save and exit)
	
		[Unit]
		Description=Personalization
		After=network-online.target

		[Service]
		Type=oneshot
		RemainAfterExit=yes
		WorkingDirectory=/boot/efi/EFI/HPE/isdeploy/
		ExecStart=/bin/bash HPE-ImageStreamer.bash

		[Install]
		WantedBy=multi-user.target

11.	Enable the service "systemctl enable personalization.service"

12.	Power off the server. 

13.	Navigate to HPE Synergy Image Streamer -> Golden Images and Click ‘Create Golden image’ 
 
14.	Select the OS volume corresponding to the server profile created for empty OS volume and choose “HPE - Foundation 1.0 - capture 	OS Volume as is” as the capture build plan. 
 
15.	HPE Synergy Image Streamer captures RHEL image and adds it as a golden image.


## Follow the below document to load driver for HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module and Golden image capture process.

- https://github.hpe.com/ImageStreamer/image-streamer-rhel/blob/v6.40/docs/HPE%20Synergy%20ImageStreamer%20Documentation%20for%20RHEL%207.6%20for%20loading%20drivers%20during%20installation%20and%20Golden%20Image%20capture.pdf

## Artifact Bundle Contents:

--------------------------------------------------------------------------------

                     File name: HPE-RHEL7-EFI-2020-04-08-v6.40.zip
            Name (in manifest): HPE-RHEL7-EFI-2020-04-08-v6.40
                   Description: ImageStreamer artifacts for RHEL7 personalization and generalization.(c) Copyright 2019-2020 Hewlett Packard Enterprise Development LP. Licensed under the Apache License, Version 2.0 (the \"License\")...
                         Dated: 2020-04-08 (18:50:36)
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

--------------------------------------------------------------------------------

                     File name: HPE-RHEL8-EFI-2020-10-27-v6.40.zip
            Name (in manifest): HPE-RHEL8-EFI-2020-10-27-v6.40
                   Description: ImageStreamer artifacts fo RHEL8 personalization and generalization.(c) Copyright 2019-2020 Hewlett Packard Enterprise Development LP. Licensed under the Apache License, Version 2.0 (the \"License\")...
                         Dated: 2020-09-08 (09:14:45)
Build Plans:

           Name: HPE-RHEL8-EFI-personalize-and-configure-NICs-LVM-2019-06-11 (Type:deploy)
    Description: Personalizes RHEL8 for XFS Partition using EFI and configures Multi NIC's  (c) Copyright 2018 -2020 Hewlett Packard Enterprise Development LP Licensed under the Apache License, Version 2.0 (the "License");...


           Name: HPE-RHEL8-EFI-personalize-and-configure-NIC-teamings-LVM-2020-04-08 (Type:deploy)
    Description: Personalizes RHEL8 for XFS Partition using EFI and configures NIC teaming (c) Copyright 2018-2020 Hewlett Packard Enterprise Development LP Licensed under the Apache License, Version 2.0 (the "License");...
Plan Scripts:

           Name: HPE-RHEL8-EFI-configure-hostname-2019-03-21 (deploy)
       FullName: 056df3ca-bc4e-4775-afe3-5834c7fdd17e_planscript.json
    Description: Configure hostname


           Name: HPE-RHEL8-EFI-configure-multiple-NICs-2019-03-21 (deploy)
       FullName: 07c92491-5287-471c-829f-be80e1f89ee1_planscript.json
    Description: Configures NICs


           Name: HPE-RHEL8-EFI-configure-users-2019-03-21 (deploy)
       FullName: 3465f01d-98af-45a0-b411-60b162cb5f0b_planscript.json
    Description: Sets root password and create user accounts


           Name: HPE-RHEL8-EFI-wrapper-2019-03-21 (deploy)
       FullName: 573bbf7f-a851-4d83-8b28-a3b8d4f8c8c1_planscript.json
    Description: This is a wrapper script where all other scripts are evoked.


           Name: HPE-RHEL8-EFI-unmount-2019-03-21 (general)
       FullName: 741f4e2c-95e1-4e83-a2e5-3794e23b0f4d_planscript.json
    Description: Unmounts the EFI partition


           Name: HPE-RHEL8-EFI-configure-partition-using-LVM-2019-05-01 (deploy)
       FullName: 8c6cf7a1-73ac-4de3-baaa-c50f27f430e9_planscript.json
    Description: LVM configuration using /boot/efi


           Name: HPE-RHEL8-EFI-configure-management-NIC-teaming-2020-04-08 (deploy)
       FullName: 94f7b3a0-a020-4842-aa55-0bf343478d39_planscript.json
    Description: Configures management NIC teaming.


           Name: HPE-RHEL8-EFI-configure-deployment-NIC-teaming-2020-04-06 (deploy)
       FullName: 95bbf32a-51bd-4718-915a-985ce92c55cd_planscript.json
    Description: Script to configure deployment interface teaming (ibftNIC teaming)


           Name: HPE-RHEL8-EFI-mount-2019-03-21 (general)
       FullName: 99ce472e-a12e-4f65-88ed-f26a730bc392_planscript.json
    Description: Mounts EFI partition (/dev/sda1) as root(/)


           Name: HPE-RHEL8-EFI-manage-security-services-2019-03-21 (deploy)
       FullName: ea0a062a-0a35-4d75-a95a-a85c9f52bbba_planscript.json
    Description: Enables/Disables SSH and Enables Selinux Security
