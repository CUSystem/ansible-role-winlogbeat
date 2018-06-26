
# WinLogBeat Install and Configure

An Ansible role that installs and configures WinLogBeat.  The configuration supports 1-way SSL.


## Prerequisites

# Windows Configuration:

Get the latest version of ConfigureRemotingForAnsible.ps1 from https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1
Run this script as Administrator on  Windows machines.


Follow instructions from :
https://docs.ansible.com/ansible/2.5/user_guide/windows_winrm.html


## Role Variables

### Download and installation (Defaults): 

    winlogbeat_download_url_base: 'https://artifacts.elastic.co/downloads/beats/winlogbeat'
    winlogbeat_download_file: 'winlogbeat-6.3.0-windows-x86_64'
    file_ext: '.zip'  # file extension for winlogbeat_download file
    winlogbeat_install_location: "C:/Program Files/Winlogbeat"

### Example ( Default) Input:

    winlogbeat_events:
      - name: Application
      - name: Security
      - name: System

### Tags and Fields can be added :


    winlogbeat_tags:
       - service-X
       - web-tier


    winlogbeat_fields:
       - env: staging
    

Fields can be set at the top-level or (by default) are under sub-directory:
   
    winlogbeat_fields_under_root: false

### Output Host options:

Output can be to Elasticsearch and/or Logstash:

    winlogbeat_output_elasticsearch_hosts:
    #  - "localhost:9200"

    winlogbeat_output_logstash_hosts:
    #  - "localhost:5000"

  
Adding hosts enables that output.  No defaults provided.  Therefore, one or both need to be configured.

### SSL options (Defaults)

    winlogbeat_ssl_certificate_authorities: #Collection
    winlogbeat_ssl_verification_mode: # none, full
    winlogbeat_ssl_renegotiation: #never, once, freely
    winlogbeat_ssl_supported_protocols: #Collection: [SSLv3, TLSv1, TLSv1.0, TLSv1.1, TLSv1.2]
    winlogbeat_ssl_cipher_suites: #Collection - See docs for available types
    winlogbeat_ssl_curve_types: #Collection - [P-256, P-384, P521]
    winlogbeat_ssl_enabled: # true, false


### Logging options (Defaults)

    winlogbeat_enable_logging: false
    winlogbeat_log_level: warning
    winlogbeat_log_dir: "{{ winlogbeat_install_location }}/{{ winblogbeat_download_file }}/logs"
    winlogbeat_log_filename: mybeat.log

### License 

The MIT License (MIT)


### Attribution

(c) Regents of the University of Colorado


