# RHEL 7.2 artifacts for ImageStreamer v3.1 release
## Note: 
- All artifact bundles in this repo are compatible with ImageStreamer v3.1 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
      
## Version History:

HPE-RHEL-7.2-2017-08-21-v3.1 
- Fixes for issues related to NIC teaming, default gateway, default route

HPE-RHEL-7.2-2017-04-20 
- Fixed issues with character encoding

HPE-RHEL-7.2-2017-03-24 
- Initial version

## Artifact Bundle Contents

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-7.2-2017-08-21-v3.1.zip
		Name (in manifest): HPE-RHEL-7.2-2017-08-21
		       Description: ImageStreamer artifacts for RHEL 7.2 personalization and generalization.
		             Dated: 2017-08-21 (18:52:14)

--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-7.2-personalize-and-NIC-teamings-LVM-BP-2017-08-21 (Type:deploy)
	Description: Personalizes RHEL 7.2 and configures NIC teaming 

	       Name: RHEL-7.2-personalize-and-configure-NICs-LVM-BP-2017-08-21 (Type:deploy)
	Description: Personalizes RHEL 7.2 and configures NICs

	       Name: RHEL-7.2-generalize-2017-06-02 (Type:capture)
	Description: Remove personalization settings from RHEL 7.2 


Plan Scripts:

	       Name: RHEL-7.2-configure-users-2017-03-15 (deploy)
	   FullName: 04cb5d8f-8a99-47f3-bdbb-8ed3d4234148_planscript.json
	Description: set root password and create user accounts


	       Name: RHEL-7.2-generalize-users-2017-03-15 (capture)
	   FullName: 50927c9c-741a-4cd8-bd8f-c6712fdeda4e_planscript.json
	Description: remove user accounts


	       Name: RHEL-7.2-manage-security-services-2017-04-20 (deploy)
	   FullName: 58ab3aca-5083-4995-8237-9ec503d8db41_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-7.2-mount-generalize-2017-03-15 (capture)
	   FullName: 7a4c3876-a5ef-4b4f-8d50-9a8970ad66a0_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-7.2-unmount-generalize-2017-03-15 (capture)
	   FullName: ae1f7d6f-1db3-4bd8-9812-5802e3407626_planscript.json
	Description: unmount RHEL partition


	       Name: RHEL-7.2-mount-and-validate-2017-03-15 (general)
	   FullName: af45b086-2aac-4dec-bae0-d54693f90db9_planscript.json
	Description: Plan Script mount to the root partition of the server along with that it will validate image to check whether it is appropriate image to use.


	       Name: RHEL-7.2-unmount-2017-03-15 (general)
	   FullName: b30a1811-b610-4e0c-a421-cf2a5445969b_planscript.json
	Description: It removes the temporary directory created during mount and unmounts from the root partition.


	       Name: RHEL-7.2-configure-hostname-2017-08-21 (deploy)
	   FullName: c2afb58c-34b6-4ac2-aa3b-10b781c895b2_planscript.json
	Description: configure hostname


	       Name: RHEL-7.2-configure-multiple-NICs-2017-03-15 (deploy)
	   FullName: c4c6b397-2a75-4f22-8915-cb909ae7bf90_planscript.json
	Description: Configures NICs.


	       Name: RHEL-7.2-configure-partition-using-LVM-2017-03-15 (deploy)
	   FullName: c734e917-ace2-4042-8a18-824d3e9cd6dc_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-7.2-configure-multiple-NIC-teaming-2017-06-02 (deploy)
	   FullName: d4e20c8e-1773-47db-a8e1-b02068cc5c86_planscript.json
	Description: configure NIC teaming


	       Name: RHEL-7.2-generalize-host-2017-03-15 (capture)
	   FullName: e70b91f0-190b-40c4-8ad7-5d0ed6c37ccb_planscript.json
	Description: Remove host configuration


	       Name: RHEL-7.2-generalize-network-2017-06-02 (capture)
	   FullName: f819b6d3-5473-4021-ac41-118abb60a694_planscript.json
	Description: Remove network settings


