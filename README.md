# sap_hana_global_configurator
The sap_hana_global_configuration ensures, that similar settings are defined onces.
## Typical example
During an installation the SID need to be set to the same value in different system roles using different variable names.

One way to get this solved is to use one variable for this unique content. For this we need to find a variable name which isn't used.

If we take the example of https://github.com/redhat-sap/sap-hana-deployment

The SID is specified with **sap_hana_deployment_hana_sid**.

If we want to configure https://github.com/redhat-sap/sap-hana-hsr we have to define **sap_hana_hsr_hana_sid**.

Asuming **sap_hana_sid** is not used, we can define it as group_var and add this variable as default to the systemroles.

If we would now set each parameter it will work as it was before.
If we would add a variable **sap_hana_sid** to the group_vars/all.yml and add

===
sap_hana_hsr_hana_sid = "{{ sap_hana_sid }}"
===

to the **default/main.yml** File It would use the SID specified once. 
