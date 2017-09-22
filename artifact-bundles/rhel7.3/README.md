# RHEL 7.3 artifacts for ImageStreamer v3.0 release
## Note: 
- All artifact bundles in this repo are compatible with ImageStreamer v3.0 release
- Click on 'Branch:' dropdown to get artifact bundles for other ImageStreamer releases

## Version History:

HPE-RHEL-7.3-2017-06-20-v3.0 
- Fixes for issues related to NIC teaming

HPE-RHEL-7.3-2017-04-20 
- Fixed issues with character encoding

HPE-RHEL-7.3-2017-03-24 
- Initial version

## Artifact Bundle Contents

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-7.3-2017-06-02-v3.0.zip
		Name (in manifest): HPE-RHEL-7.3-2017-06-02
		       Description: ImageStreamer artifacts for RHEL 7.3 personalization and generalization 
		             Dated: 2017-06-02 (06:09:02)

--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-7.3-personalize-and-NIC-teamings-LVM-BP-2017-06-02 (Type:deploy)
	Description: Personalize RHEL 7.3 and configure NIC teamings.

	       Name: RHEL-7.3-personalize-and-configure-NICs-LVM-BP-2017-04-20 (Type:deploy)
	Description: Personalize RHEL 7.3 and configure NICs.

	       Name: RHEL-7.3-generalize-2017-06-01 (Type:capture)
	Description: Remove personalization settings from RHEL 7.3.


Plan Scripts:

	       Name: RHEL-7.3-unmount-2017-03-15 (general)
	   FullName: 0138cd7c-27de-4d47-82c9-1a380ba40fe2_planscript.json
	Description: It removes the temporary directory created during mount and unmounts from the root partition.


	       Name: RHEL-7.3-configure-partition-using-LVM-2017-03-15 (deploy)
	   FullName: 1b8e1093-e245-4b02-904c-695feffa9668_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-7.3-mount-generalize-2017-03-15 (capture)
	   FullName: 22d800fa-bcee-4b65-851c-95620aaf945a_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-7.3-generalize-network-2017-06-01 (capture)
	   FullName: 306337e1-c65f-4ced-8a49-f68a20d119af_planscript.json
	Description: remove network configuration


	       Name: RHEL-7.3-configure-hostname-2017-03-15 (deploy)
	   FullName: 73a97210-c791-4e75-b9f3-f62387343237_planscript.json
	Description: configure hostname


	       Name: RHEL-7.3-manage-security-services-2017-04-20 (deploy)
	   FullName: 7a42a680-b00b-4196-b5ca-c020b2a17d0b_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-7.3-generalize-users-2017-03-15 (capture)
	   FullName: 7f5b919f-ccbf-4998-83f1-654217125eb9_planscript.json
	Description: remove user settings


	       Name: RHEL-7.3-configure-multiple-NIC-teaming-2017-06-02 (deploy)
	   FullName: 8e5df19c-598a-40b6-9d0c-ac2ac7eabbdf_planscript.json
	Description: configure NIC teaming


	       Name: RHEL-7.3-unmount-generalize-2017-03-15 (capture)
	   FullName: 93ef09dd-33e4-40c6-998a-5ac1bf1abae1_planscript.json
	Description: unmount RHEL partition after generalization


	       Name: RHEL-7.3-configure-swap-2017-06-02 (deploy)
	   FullName: c796495f-cf3e-4aeb-8928-41bfa8f1d137_planscript.json
	Description: Configure entire local disk as swap device


	       Name: RHEL-7.3-configure-multiple-NICs-2017-03-15 (deploy)
	   FullName: cb2aafd4-3771-4b48-971b-a75a274d6c94_planscript.json
	Description: Configures NICs.


	       Name: RHEL-7.3-generalize-host-2017-03-15 (capture)
	   FullName: e9c771c7-b249-47ca-92c3-7b49bb7dcb82_planscript.json
	Description: remove host configuration


	       Name: RHEL-7.3-configure-users-2017-03-15 (deploy)
	   FullName: ea0de5a8-6e9e-43a5-8d33-d4705da67698_planscript.json
	Description: Helps to change the root password and to add a new user to the server based on user input.


	       Name: RHEL-7.3-mount-and-validate-2017-03-15 (general)
	   FullName: f3579f13-6365-439c-87e6-9e4e95d8d0eb_planscript.json
	Description: mount RHEL partition and validate its contents


