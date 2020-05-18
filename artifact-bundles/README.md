# RHEL 7.x and 8 artifacts for ImageStreamer v5.2 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v5.2 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases

## EFI based artifacts

With the EFI based artifacts, ImageStreamer can support all the filesystems including XFS/BTRFS for RHEL Operating system.
This was not possible earlier because, Guestfish, used to customize the boot volume of the operating system, did not support XFS/BTRFS. 

Until now the root partition was mounted in the plan scripts, but now, to enable deployment using FAT32,  mount the partition (/boot/efi) and run the plan scripts through it for personalization, which provides support for all the filesystems.

## Version history


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


## Follow the below document to load driver for HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module and Golden image capture process.

- https://github.com/HewlettPackard/image-streamer-rhel/blob/v5.2/docs/HPE%20Synergy%20ImageStreamer%20Documentation%20for%20RHEL%207.6%20for%20loading%20drivers%20during%20installation%20and%20Golden%20Image%20capture.pdf


## Artifact Bundle Contents:

--------------------------------------------------------------------------------

	            File name: HPE-RHEL7-EFI-2019-06-11-v5.0.zip
		Name (in manifest): HPE-RHEL7-EFI-2019-06-11-v5.0
		       Description: ImageStreamer artifacts for RHEL 7.X personalization and generalization.
		             Dated: 2019-06-11 (11:22:36)

--------------------------------------------------------------------------------

Build Plans:

	       Name: HPE-RHEL7-EFI-personalize-and-configure-NICs-LVM-2019-06-11 (Type:deploy)
	Description: Personalizes RHEL 7.X for XFS Partition using EFI and configures Multi NIC's  


	       Name: HPE-RHEL7-EFI-personalize-and-configure-NIC-teamings-LVM-2019-06-07 (Type:deploy)
	Description: Personalizes RHEL 7.X for XFS Partition using EFI and configures NIC teaming 



Plan Scripts:

	       Name: HPE-RHEL7-EFI-unmount-2019-03-21 (general)
	   FullName: 29842898-0f3e-4a95-9d64-9c100b06a968_planscript.json
	Description: Unmounts the EFI partition


	       Name: HPE-RHEL7-EFI-configure-management-NIC-teaming-2019-03-25 (deploy)
	   FullName: 4545a4ba-490f-487f-b8f9-263b3bf426a9_planscript.json
	Description: Configures management NIC teaming.


	       Name: HPE-RHEL7-EFI-configure-hostname-2019-03-21 (deploy)
	   FullName: 4d4778e2-ced4-4864-872d-04f4b6fcb9e5_planscript.json
	Description: Configure hostname


	       Name: HPE-RHEL7-EFI-configure-partition-using-LVM-2019-05-01 (deploy)
	   FullName: 5844db39-92fe-4707-b614-b56afda6cd9b_planscript.json
	Description: LVM configuration using /boot/efi


	       Name: HPE-RHEL7-EFI-wrapper-2019-03-21 (deploy)
	   FullName: 77d9557c-18f0-4f7d-a1e3-b2b4a8b91f9d_planscript.json
	Description: This is a wrapper script where all other scripts are evoked.


	       Name: HPE-RHEL7-EFI-configure-multiple-NICs-2019-03-21 (deploy)
	   FullName: 7f436449-921d-46d6-adaf-e638174b165b_planscript.json
	Description: Configures NICs


	       Name: HPE-RHEL7-EFI-configure-users-2019-03-21 (deploy)
	   FullName: 8677fc04-6061-401e-9e5a-87f8756d7714_planscript.json
	Description: Sets root password and create user accounts


	       Name: HPE-RHEL7-EFI-configure-deployment-NIC-teaming-2019-03-25 (deploy)
	   FullName: b6f243bd-a9ab-443e-905b-b9a4638a8591_planscript.json
	Description: Script to configure deployment interface teaming (ibftNIC teaming)


	       Name: HPE-RHEL7-EFI-mount-2019-03-21 (general)
	   FullName: c3de07cc-8138-48d9-be76-c80a4875fc35_planscript.json
	Description: Mounts EFI partition (/dev/sda1) as root(/)


	       Name: HPE-RHEL7-EFI-manage-security-services-2019-03-21 (deploy)
	   FullName: eccaa17b-b9ca-45a6-a317-181965494101_planscript.json
	Description: Enables/Disables SSH and Enables Selinux Security



