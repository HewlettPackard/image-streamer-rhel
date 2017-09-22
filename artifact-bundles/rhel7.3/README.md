# RHEL 7.3 artifacts for ImageStreamer v3.1 release
## Note: 
- All artifact bundles in this repo are compatible with ImageStreamer v3.1 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
      
## Version History:

HPE-RHEL-7.3-2017-08-21-v3.1 
- Fixes for issues related to NIC teaming, default gateway, default route

HPE-RHEL-7.3-2017-04-20 
- Fixed issues with character encoding

HPE-RHEL-7.3-2017-03-24 
- Initial version


## Artifact Bundle Contents

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-7.3-2017-08-21-v3.1.zip
		Name (in manifest): HPE-RHEL-7.3-2017-08-21
		       Description: ImageStreamer artifacts for RHEL 7.3 personalization and generalization 
		             Dated: 2017-08-21 (13:29:54)

--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-7.3-personalize-and-configure-NICs-LVM-BP-2017-08-21 (Type:deploy)
	Description: Personalize RHEL 7.3 and configure NICs.

	       Name: RHEL-7.3-personalize-and-NIC-teamings-LVM-BP-2017-08-21 (Type:deploy)
	Description: Personalize RHEL 7.3 and configure NIC teamings.

	       Name: RHEL-7.3-generalize-2017-06-01 (Type:capture)
	Description: Remove personalization settings from RHEL 7.3.


Plan Scripts:

	       Name: RHEL-7.3-configure-multiple-NIC-teaming-2017-06-02 (deploy)
	   FullName: 062e71b3-0d70-4ff1-aae3-ab77b6954131_planscript.json
	Description: configure NIC teaming


	       Name: RHEL-7.3-mount-generalize-2017-03-15 (capture)
	   FullName: 18700681-a070-44e7-964f-e9d17f3d5537_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-7.3-generalize-network-2017-06-01 (capture)
	   FullName: 1ae9d7f5-a82d-4bcd-976b-0f725953db3f_planscript.json
	Description: remove network configuration


	       Name: RHEL-7.3-configure-hostname-2017-08-21 (deploy)
	   FullName: 1fb84991-20f2-4835-ab8c-a66ad3930fe3_planscript.json
	Description: configure hostname


	       Name: RHEL-7.3-manage-security-services-2017-04-20 (deploy)
	   FullName: 25c42e19-ff38-4afa-96de-b8fd6c2a3f11_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-7.3-generalize-host-2017-03-15 (capture)
	   FullName: 6fe420d8-f102-4e62-99fc-81e6d14a95df_planscript.json
	Description: remove host configuration


	       Name: RHEL-7.3-configure-users-2017-03-15 (deploy)
	   FullName: 703196a6-17a0-488d-afa2-e08ad58b679b_planscript.json
	Description: Helps to change the root password and to add a new user to the server based on user input.


	       Name: RHEL-7.3-mount-and-validate-2017-03-15 (general)
	   FullName: 766f9e96-2465-4694-8119-a04507a9c6a0_planscript.json
	Description: mount RHEL partition and validate its contents


	       Name: RHEL-7.3-configure-partition-using-LVM-2017-03-15 (deploy)
	   FullName: 9a3014de-ded4-477e-9e3b-e932cb6207c2_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-7.3-configure-multiple-NICs-2017-03-15 (deploy)
	   FullName: adbe884e-1e49-47f2-a2da-a085e6e4bbcf_planscript.json
	Description: Configures NICs.


	       Name: RHEL-7.3-generalize-users-2017-03-15 (capture)
	   FullName: ce476a6a-77a5-4d34-9bcb-dff49db48592_planscript.json
	Description: remove user settings


	       Name: RHEL-7.3-unmount-2017-03-15 (general)
	   FullName: d516f0fb-b4eb-4a44-80ea-813ab59f841f_planscript.json
	Description: It removes the temporary directory created during mount and unmounts from the root partition.


	       Name: RHEL-7.3-unmount-generalize-2017-03-15 (capture)
	   FullName: ff7f8be4-2fc0-410a-8f02-f979dabc9522_planscript.json
	Description: unmount RHEL partition after generalization




