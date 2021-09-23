Generate Satellite Report
=========

This role generates a Satellite report via API and stores the resuls in the variable `satellite_report_data`.

Role Variables
--------------

```yaml
---
# defaults file for generate_satellite_report

# FQDN of Satellite host. Mandatory.
satellite_host:
# Controls whether to validate certificates of server or not. Optional, default is True.
satellite_validate_certs:
# ID number of report template to generate report from. Mandatory.
satellite_report_id:
# Username to logon to Satellite. Mandatory.
satellite_username:
# Password to logon to Satellite. Mandatory.
satellite_password:
# Input values for report template. Optional.
# Note: This will be sent to the Satellite server API as the body of a HTTP POST message so must be JSON formatted.
satellite_input_values: 

# Example:
satellite_input_values: |
  {
      "input_values":{ 
          "Hosts": "name ==  server1.example.local or name ==  server2.example.local"        
      }
  }  


# Controls whether the job should pause before generating the report. Useful when running the role as part of a workflow
# and need to allow a few mins for stats to update in Satellite before generating a report. Optional. True/False, defaults to False
pause_before_report: False

# Controls how long in minutes to pause for. Optional. Integer, default '3'.
pause_mins: 3
```


Example Playbook
----------------

```yaml
---
- name: Generate Satellite Report
  hosts: localhost
  connection: local
  gather_facts: no
  tasks:
    - name: Apply generate_satellite_report role
      include_role:
        name: generate_satellite_report

```
License
-------

BSD

Author Information
------------------

Blake Douglas, blake@redhat.com