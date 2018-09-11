# RHEL 7.x artifacts for ImageStreamer v4.1 release

## Note:
- All artifact bundles in this repo are compatible with ImageStreamer v4.1 release
- Click on 'Branch:' drop down menu on this page to get artifact bundles for other ImageStreamer releases
- The following RHEL versions are supported
	- RHEL 7.2
	- RHEL 7.3
	- RHEL 7.4

## Version History:
HPE-RHEL-2018-09-11-v4.1.zip
   - Type has been updated for CAs on buildplan 
   
   	"DomainName" as FQDN,  "TotalNICTeamings" as Number
   - One line description has been updated for CAs on buildplan
   
   	"DomainName","TotalNICTeamings","New User","NewRootPassword","NewUserPassword","NICTeam0Name","NICTeam1Name"
   - Files chnaged in this version :
		- RHEL-personalize-and-NIC-teamings-LVM-BP-2018-09-11
		- RHEL-personalize-and-configure-NICs-LVM-BP-2018-09-11
   

## Artifact Bundle Contents:

--------------------------------------------------------------------------------
         File name: HPE-RHEL-2018-09-11-v4.1.zip
         Name (in manifest): HPE-RHEL-2018-09-11-v4.1
         Description: ImageStreamer artifacts for RHEL 7.X personalization and generalization.
         Dated: 2018-09-11 (13:36.03)
--------------------------------------------------------------------------------

Build Plans:

	       Name: RHEL-personalize-and-NIC-teamings-LVM-BP-2018-09-11 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC teaming 


	       Name: RHEL-generalize-2018-06-27 (Type:capture)
	Description: Remove personalization settings from RHEL 7.X 


	       Name: RHEL-personalize-and-configure-NICs-LVM-BP-2018-09-11 (Type:deploy)
	Description: Personalizes RHEL 7.X and configures NIC teaming  



Plan Scripts:

	       Name: RHEL-mount-generalize-2017-12-12 (capture)
	   FullName: 12a427c2-3571-4d20-9b65-274841e57244_planscript.json
	Description: mount RHEL partition for generalization


	       Name: RHEL-manage-security-services-2017-12-12 (deploy)
	   FullName: 16769622-aaae-4125-b31d-254982f926b6_planscript.json
	Description: Enables or Disables the services.


	       Name: RHEL-configure-hostname-2017-12-12 (deploy)
	   FullName: 1ed81eb7-5190-418b-b6e5-b3258605401b_planscript.json
	Description: configure hostname


	       Name: RHEL-generalize-users-2018-06-27 (capture)
	   FullName: 21687863-bc4b-4bf0-9b19-f62551537727_planscript.json
	Description: remove user accounts


	       Name: RHEL-mount-and-validate-2017-12-12 (general)
	   FullName: 25985015-8f19-4c24-b587-3044442d0ef1_planscript.json
	Description: mount the root partition of the server and validate image against invalid image captures


	       Name: RHEL-configure-multiple-NICs-2017-12-15 (deploy)
	   FullName: 5b79d02f-defe-4dde-af76-a3e28dafc07a_planscript.json
	Description: Configures NICs.


	       Name: RHEL-generalize-host-2017-12-12 (capture)
	   FullName: 796109d7-15e2-4e62-80f0-4819ff9eeb06_planscript.json
	Description: Remove host configuration


	       Name: RHEL-configure-deployment-NIC-teaming-2017-12-12 (deploy)
	   FullName: 81c72a74-5f95-4648-896e-56c8b46f6887_planscript.json
	Description: script to configure deployment interface teaming (also known as ibftNic teaming)


	       Name: RHEL-configure-partition-using-LVM-2017-12-12 (deploy)
	   FullName: 936eb0b9-ffb5-4783-bbcf-3822883461b1_planscript.json
	Description: Creates a partition on the disk based on user requirement.


	       Name: RHEL-unmount-2017-12-12 (general)
	   FullName: 96667106-3411-42af-b624-d1a7d28e0ff4_planscript.json
	Description: cleans up the temporary directory created during mount and unmounts the root partition.


	       Name: RHEL-unmount-generalize-2017-12-12 (capture)
	   FullName: b55efd80-82f8-4c48-b093-5dabeed19211_planscript.json
	Description: unmount RHEL partition


	       Name: RHEL-configure-users-2018-06-27 (deploy)
	   FullName: e16e84a4-5911-4581-afa8-e4310e583c88_planscript.json
	Description: set root password and create user accounts


	       Name: RHEL-configure-management-NIC-teaming-2018-02-09 (deploy)
	   FullName: f092e7a6-17aa-4009-b913-69a216b18fe6_planscript.json
	Description: configures management NIC teaming


	       Name: RHEL-generalize-network-2017-12-12 (capture)
	   FullName: f21915aa-4d41-4272-bcd4-5b7169474657_planscript.json
	Description: Remove network settings
