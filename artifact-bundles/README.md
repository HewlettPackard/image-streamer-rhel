# RHEL 7.x artifacts for ImageStreamer v4.2 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v4.2 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
- The following RHEL versions are supported
	- RHEL 7.2
	- RHEL 7.3
	- RHEL 7.4

## Version History:
HPE-RHEL-2018-09-11-v4.2.zip
   - Type has been updated for CAs on buildplan 
   
   	"DomainName" as FQDN,  "TotalNICTeamings" as Number
   - One line description has been updated for CAs on buildplan
   
   	"DomainName","TotalNICTeamings","New User","NewRootPassword","NewUserPassword","NICTeam0Name","NICTeam1Name"
   - Files changed in this version :
		- RHEL-personalize-and-NIC-teamings-LVM-BP-2018-09-11
		- RHEL-personalize-and-configure-NICs-LVM-BP-2018-09-11
   

## Artifact Bundle Contents:

--------------------------------------------------------------------------------

	            File name: HPE-RHEL-2018-09-11-v4.2.zip
		Name (in manifest): HPE-RHEL-2018-09-11-v4.2
		       Description: ImageStreamer artifacts for RHEL 7.X personalization and generalization.
		             Dated: 2018-09-11 (06:13:36)

--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-personalize-and-configure-NICs-LVM-BP-2018-09-11 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC teaming 


	       Name: RHEL-personalize-and-NIC-teamings-LVM-BP-2018-09-11 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC teaming 


	       Name: RHEL-generalize-2018-06-27 (Type:capture)
	Description: Remove personalization settings from RHEL 7.X 



Plan Scripts:

	       Name: RHEL-configure-multiple-NICs-2017-12-15 (deploy)
	   FullName: 127a4738-7c5d-477e-9257-b246f6896391_planscript.json
	Description: Configures NICs.


	       Name: RHEL-configure-users-2018-06-27 (deploy)
	   FullName: 20390d90-977e-49a8-988f-0419fb98c94b_planscript.json
	Description: set root password and create user accounts


	       Name: RHEL-generalize-host-2017-12-12 (capture)
	   FullName: 21b2afc9-dede-4ded-a3aa-270d04f53210_planscript.json
	Description: Remove host configuration


	       Name: RHEL-configure-partition-using-LVM-2017-12-12 (deploy)
	   FullName: 2847707d-25af-443f-b747-496789d4f339_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-configure-hostname-2017-12-12 (deploy)
	   FullName: 2c50e880-9f7e-48e6-a538-115ab4e9a4fe_planscript.json
	Description: configure hostname


	       Name: RHEL-configure-deployment-NIC-teaming-2017-12-12 (deploy)
	   FullName: 48c0785a-b41a-419c-995d-0ef65cc1cd91_planscript.json
	Description: script to configure deployment interface teaming (also known as ibftNic teaming)


	       Name: RHEL-unmount-2017-12-12 (general)
	   FullName: 7632ec2a-a44d-4497-a925-a80f1269f1cb_planscript.json
	Description: cleans up the temporary directory created during mount and unmounts the root partition.


	       Name: RHEL-generalize-users-2018-06-27 (capture)
	   FullName: a034bf3e-39cd-4821-9eb2-4e4e21fb6284_planscript.json
	Description: remove user accounts


	       Name: RHEL-manage-security-services-2017-12-12 (deploy)
	   FullName: a7039ed9-d47a-4f8b-9f93-c9f8e78170a9_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-mount-generalize-2017-12-12 (capture)
	   FullName: bcef704c-df33-4185-82d1-ab3e2278b8ce_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-configure-management-NIC-teaming-2018-02-09 (deploy)
	   FullName: de1c792c-783a-465a-b785-01359d4247f4_planscript.json
	Description: configures management NIC teaming


	       Name: RHEL-generalize-network-2017-12-12 (capture)
	   FullName: ecc0dd0d-8546-4c40-b555-b822fcc1168c_planscript.json
	Description: Remove network settings


	       Name: RHEL-mount-and-validate-2017-12-12 (general)
	   FullName: f194effc-c2c3-48ea-abea-0ffe8665176c_planscript.json
	Description: mount the root partition of the server and validate image against invalid image captures


	       Name: RHEL-unmount-generalize-2017-12-12 (capture)
	   FullName: f5593a3e-d10c-49eb-8cba-c6d00491f66a_planscript.json
	Description: unmount RHEL partition
