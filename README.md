# Redhat-Subscription-Registration-for-SAP-HANA
 Red Hat Subscription Registration Playbook
 Overview
This Ansible playbook accomplishes two main tasks:

Sets the system locale to C.UTF-8 for correct character encoding.

Registers the system with Red Hat Subscription Manager (RHSM) to enable access to Red Hat repositories and updates. You can choose between username/password or activation key methods for registration.

Requirements
Ansible 2.9 or higher is required.

The target machine should be a RHEL 8/9 system.

Root privileges on the target machine.

Red Hat Subscription Manager (RHSM) installed on the target system.

Variables
These variables can be customized in the playbook or via the inventory file:


Variable Name	Description	Default Value
rhsm_username	Red Hat username for registration.	"" (empty string)
rhsm_password	Red Hat password for registration (if using username/password method).	"" (empty string)
rhsm_activationkey	Activation key for registration (if using activation key method).	"" (empty string)
rhsm_org_id	Organization ID for registration (required for activation key).	"" (empty string)
rhsm_auto_attach	Automatically attach a subscription if possible.	true
rhsm_force_register	Force system unregister if already registered (optional).	true
system_locale	Locale to set on the system (default is C.UTF-8).	C.UTF-8
Playbook Structure
This playbook includes the following tasks:

Set System Locale: Configures /etc/locale.conf and optionally /etc/profile.d/locale.sh to set the system locale to C.UTF-8.

Unregister System: If a system is already registered and rhsm_force_register is enabled, it unregisters the system before re-registering.

Register with RHSM:

If using username/password, it registers with RHSM using subscription-manager register.

If using activation key, it registers with the given key and org ID.


