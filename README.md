Nagios-WordPress-Update
===============

A Nagios plugin to check for WordPress version updates on a remote server without the use of NRPE.

[Nagios Exchange](https://exchange.nagios.org/directory/Plugins/CMS-and-Blog-Software/Wordpress/Check-WordPress-Update/details)

How to use:

- Upload wp-version.php to your WordPress root installation
- Include the IP address of your Nagios installation in the script
- Copy check\_wp\_update to your Nagios plugins folder. For me, it's on /usr/lib64/nagios/plugins
- Create a service command template
- Create a service check on your host

__Command Template__

	define command{
	        command_name    check_wp_update
	        command_line    $USER1$/check_wp_update $ARG1$
	        }

__Service Check__

	define service{
	        use                     generic-service
	        host_name               example.com
	        service_description     My WordPress Install
	        check_command           check_wp_update!http://example.com/wp-version.php
	        }

Inspired by check\_wp\_version by @hteske. Original [here](http://exchange.nagios.org/directory/Plugins/CMS-and-Blog-Software/Wordpress/check_wp_version/details)
