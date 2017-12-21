# RHEL 7.x artifacts for ImageStreamer v4.0 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v4.0 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases

## Artifact Bundle Contents:

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-2017-12-15-v4.0.zip
		Name (in manifest): HPE-RHEL-2017-12-15-v4.0
		       Description: ImageStreamer artifacts for RHEL 7.X personalization and generalization.
		             Dated: 2017-10-31 (04:29:13)

--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-personalize-and-NIC-teamings-LVM-BP-2017-12-15 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC teaming 


	       Name: RHEL-personalize-and-configure-NICs-LVM-BP-2017-12-15 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC 


	       Name: RHEL-generalize-2017-12-12 (Type:capture)
	Description: Remove personalization settings from RHEL 7.X 



Plan Scripts:

	       Name: RHEL-generalize-users-2017-12-12 (capture)
	   FullName: 0a8e17a9-54cd-4de4-b129-9666146be498_planscript.json
	Description: remove user accounts


	       Name: RHEL-generalize-network-2017-12-12 (capture)
	   FullName: 15a15e9e-40d4-4c7f-98e5-88c7f2724a25_planscript.json
	Description: Remove network settings


	       Name: RHEL-configure-deployment-NIC-teaming-2017-12-12 (deploy)
	   FullName: 37a84b4d-7ca0-440f-8533-ea7a2c9c04f0_planscript.json
	Description: script to configure deployment interface teaming (also known as ibftNic teaming)


	       Name: RHEL-generalize-host-2017-12-12 (capture)
	   FullName: 53e951b1-68b4-461c-9476-211fd26bbe8c_planscript.json
	Description: Remove host configuration


	       Name: RHEL-configure-multiple-NICs-2017-12-15 (deploy)
	   FullName: 5c63a1d5-88f5-4804-ac1e-52a0e7ad1f1c_planscript.json
	Description: Configures NICs.


	       Name: RHEL-unmount-2017-12-12 (general)
	   FullName: 62dad4df-6ba6-48e3-857e-70909e2c3bf3_planscript.json
	Description: cleans up the temporary directory created during mount and unmounts the root partition.


	       Name: RHEL-configure-hostname-2017-12-12 (deploy)
	   FullName: 6f68f406-e5dc-41b2-b68c-d44c05c39008_planscript.json
	Description: configure hostname


	       Name: RHEL-mount-generalize-2017-12-12 (capture)
	   FullName: 716fa3cb-1e0e-417e-9038-ddad4c1e1358_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-manage-security-services-2017-12-12 (deploy)
	   FullName: 7851c6e7-ac5c-44f4-8cac-3b4431be8080_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-configure-partition-using-LVM-2017-12-12 (deploy)
	   FullName: 90b21c58-b570-475b-9c89-957e2534ba71_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-unmount-generalize-2017-12-12 (capture)
	   FullName: 9677b2b7-db87-4255-bbf5-e17f05147bc9_planscript.json
	Description: unmount RHEL partition


	       Name: RHEL-configure-users-2017-12-12 (deploy)
	   FullName: b2379c3e-d4c8-40d8-80b4-bac43b94c673_planscript.json
	Description: set root password and create user accounts


	       Name: RHEL-configure-management-NIC-teaming-2017-12-15 (deploy)
	   FullName: f01ea585-7a3e-4d20-bf7d-1dcd2d14df5a_planscript.json
	Description: configures management NIC teaming


	       Name: RHEL-mount-and-validate-2017-12-12 (general)
	   FullName: f690745e-f479-4794-9d7d-4ab24b637ddf_planscript.json
	Description: mount the root partition of the server and validate image against invalid image captures


