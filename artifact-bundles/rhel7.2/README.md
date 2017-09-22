# RHEL 7.2 artifacts for ImageStreamer v3.0 release
## Note: 
- All artifact bundles in this repo are compatible with ImageStreamer v3.0 release
- Click on 'Branch:' dropdown to get artifact bundles for other ImageStreamer releases

## Version History:

HPE-RHEL-7.2-2017-06-20-v3.0 
- Fixes for issues related to NIC teaming

HPE-RHEL-7.2-2017-04-20 
- Fixed issues with character encoding

HPE-RHEL-7.2-2017-03-24 
- Initial version



## Artifact Bundle Contents

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-7.2-2017-06-02-v3.0.zip
		Name (in manifest): HPE-RHEL-7.2-2017-06-02
		       Description: ImageStreamer artifacts for RHEL 7.2 personalization and generalization.
		             Dated: 2017-06-02 (07:04:29)

--------------------------------------------------------------------------------


Build Plans:

	       Name: RHEL-7.2-generalize-2017-06-02 (Type:capture)
	Description: Remove personalization settings from RHEL 7.2 

	       Name: RHEL-7.2-personalize-and-NIC-teamings-LVM-BP-2017-06-02 (Type:deploy)
	Description: Personalizes RHEL 7.2 and configures NIC teaming 

	       Name: RHEL-7.2-personalize-and-configure-NICs-LVM-BP-2017-04-20 (Type:deploy)
	Description: Personalizes RHEL 7.2 and configures NICs



Plan Scripts:

	       Name: RHEL-7.2-configure-swap-2017-06-02 (deploy)
	   FullName: 17cdf37d-dfaa-4484-99a5-fb3f3bc9f050_planscript.json
	Description: Configure entire local disk as swap device


	       Name: RHEL-7.2-manage-security-services-2017-04-20 (deploy)
	   FullName: 1ab27051-51eb-4a4e-9249-644a6993f2ae_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-7.2-mount-generalize-2017-03-15 (capture)
	   FullName: 1ae20a6b-4e43-4d1f-a11f-fd553017b2de_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-7.2-configure-users-2017-03-15 (deploy)
	   FullName: 1f59698c-fa48-40a3-887c-e07f2f9d806d_planscript.json
	Description: set root password and create user accounts


	       Name: RHEL-7.2-configure-multiple-NICs-2017-03-15 (deploy)
	   FullName: 44c5340b-633c-4361-b8ab-e2dc3e4b4dc1_planscript.json
	Description: Configures NICs.


	       Name: RHEL-7.2-generalize-network-2017-06-02 (capture)
	   FullName: 46408664-56e1-4477-924e-d25c7337f27e_planscript.json
	Description: Remove network settings


	       Name: RHEL-7.2-unmount-generalize-2017-03-15 (capture)
	   FullName: 551a6565-e15e-428c-ba63-bcd21c687d14_planscript.json
	Description: unmount RHEL partition


	       Name: RHEL-7.2-configure-partition-using-LVM-2017-03-15 (deploy)
	   FullName: 87d7bb67-8f27-46cd-bff8-02f731da9617_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-7.2-generalize-host-2017-03-15 (capture)
	   FullName: 88b2217e-baca-413c-a8f0-88b6bd617fc8_planscript.json
	Description: Remove host configuration


	       Name: RHEL-7.2-configure-multiple-NIC-teaming-2017-06-02 (deploy)
	   FullName: 97a47f3e-ed90-49bb-b91a-897052da4280_planscript.json
	Description: configure NIC teaming


	       Name: RHEL-7.2-generalize-users-2017-03-15 (capture)
	   FullName: ab2de93a-c000-4f25-9657-f1c746775399_planscript.json
	Description: remove user accounts


	       Name: RHEL-7.2-mount-and-validate-2017-03-15 (general)
	   FullName: be2342db-e527-4776-9f02-98c64ed61edb_planscript.json
	Description: Plan Script mount to the root partition of the server along with that it will validate image to check whether it is appropriate image to use.


	       Name: RHEL-7.2-configure-hostname-2017-03-15 (deploy)
	   FullName: defad161-70ae-42c0-9dab-d6ca9d5a9259_planscript.json
	Description: configure hostname


	       Name: RHEL-7.2-unmount-2017-03-15 (general)
	   FullName: fded07b5-5f39-4f58-8394-5fe49def153c_planscript.json
	Description: It removes the temporary directory created during mount and unmounts from the root partition.


