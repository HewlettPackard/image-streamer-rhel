# RHEL 7.x artifacts for ImageStreamer v5.0 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v5.0 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
- The following RHEL versions are supported:
	- RHEL 7.2
	- RHEL 7.3
	- RHEL 7.4
	- RHEL 7.6
	
## Version History:

HPE-RHEL7-EFI-2019-06-11-v5.0.zip
   - RHEL7 Artifact bundle for EFI based deployments. 

## EFI based artifacts

With the EFI based artifacts, ImageStreamer can support all the filesystems including XFS/BTRFS for RHEL Operating System.
This was not possible earlier because, Guestfish, used to customize the boot volume of the operating system, did not support XFS/BTRFS. 

Until now the root partition was mounted, but now, to enable UEFI based deployment, the EFI partition, (/boot/efi) is mounted using the plan scripts for personalization, which provides support for all the filesystems.

# Prerequisite for using EFI Based Artifact bundle

## Note: 
- ***A new Golden Image needs to be created for using EFI based artifact bundle. Any existing Golden Images created using earlier releases of artifact bundle will not work with EFI artifact bundle. Follow the below steps to capture the Golden Image for RHEL7.***

( In case of HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module hardware, follow the steps given in the linked document to load the driver and capture the golden image.
https://github.com/HewlettPackard/image-streamer-rhel/blob/v5.0/docs/HPE%20Synergy%20ImageStreamer%20Documentation%20for%20RHEL%207.6%20for%20loading%20drivers%20during%20installation%20and%20Golden%20Image%20capture.pdf )

- If you do not have a external hard drive attached to the blade please leave the default "disabled" option of filesystem attribute as is. Please make sure you change Filesystem Attribute in the Server Profile creation page to desired filesystem type "only when you have a external drive attached to the blade".

- LVM should be created at the time of installing the OS, on the bare metal, before image capture is done. The Filesystem type attribute in the Server Profile Page will not create LVM on the golden image which gets mounted, at the time of deployment.


## Golden Image creation for EFI based deployment of RHEL 7:

1.	Ensure that you have access to RHEL 7 ISO installation file containing iSCSI device drivers.

2.	Create a server profile with “HPE - Foundation 1.0 - create empty OS Volume” as OS Deployment plan and any available server 		hardware. Set an appropriate value for volume size in MiB units. The HPE Synergy Server will be configured for access to this 		empty OS Volume.

3.	Launch iLO Integrated Remote Console of this server and set RHEL 7 ISO file as virtual CD-ROM/DVD image file. Power on the 		server.

4.	RHEL installation starts and RHEL installer detects the configured empty OS Volume as an iSCSI disk device. Select this iSCSI 		disk device as the target for RHEL installation.

5.	Follow onscreen instructions and complete the RHEL installation.

6.	After the OS boots up Create the following directories.

      -	mkdir /boot/efi/EFI/HPE
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy/scripts
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy/tmp
      -	mkdir –p /boot/efi/EFI/HPE/isdeploy/data

7.	Modify /etc/rc.d/rc.local. Add below line

      -	sh /boot/efi/EFI/HPE/isdeploy/HPE-ImageStreamer.bash
      - service ibftT start ( ## Note: Add this line only if using either of the following setups - HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module )

8.	Change permission of the rc.local file. (chmod 755 /etc/rc.d/rc.local)

9.	Edit /boot/efi/EFI/redhat/grub.cfg and change the hardcoded IP and MAC to ip=ibft (  ## Note: Make this change only if using either of the following setups - HPE Vitual Connect SE 100Gb F32 Module or HPE Synergy 50Gb Interconnect Link Module )

10.	Power off the server. 

11.	Navigate to HPE Synergy Image Streamer -> Golden Images and Click ‘Create Golden image’ 
 
12.	Select the OS volume corresponding to the server profile created for empty OS volume and choose “HPE - Foundation 1.0 - capture 	OS Volume as is” as the capture build plan. 
 
13.	HPE Synergy Image Streamer captures RHEL image and adds it as a golden image.


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



