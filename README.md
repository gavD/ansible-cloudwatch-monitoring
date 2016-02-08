Cloudwtach monitoring
=========

This role make easier installation and configuration of the AWS script intended to monitor  memory and disk usage in cloudwatch console. 


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

- cw_script_download_url : URL to download AWS cloudwatch scripts
	* Type : string
	* Default : http://aws-cloudwatch.s3.amazonaws.com/downloads/CloudWatchMonitoringScripts-1.2.1.zip

- cw_install_dir : Folder where scripts will be installed
	* Type : string
	* Default : /opt/aws-scripts-mon/

- cw_options : Arguments used when calling cloudwatch script
	* Type : string
	* Default : --disk-space-util  --disk-path=/ --disk-space-used --disk-space-avail --swap-util --swap-used --mem-util --mem-used --mem-avail

- cw_cron_minute : Frequency (in minutes) of data reporting to cloudwatch. Must be written with crond syntax. You may want to set it to "*" if you are using detailled monitoring for your EC2 instances, to send monitoring data every 5 minutes.
	* Type : string
	* Default : "*/5"

Dependencies
------------


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: ansible-cloudwatch-monitoring, cw_cron_minute: "*/5" }

License
-------

BSD

Author Information
------------------

email : pauchet.valentin at gmail.com

