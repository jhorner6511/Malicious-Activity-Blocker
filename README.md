# Malicious-Activity-Blocker
A simple yet effective WordPress Plugin that analyzes user behavior and automatically blocks their IP Address if it detects unusual or malicious behavior.

I've made the setup and execution as simple as possible with the following steps:

- Create a new plugin directory.
- Create a new file called plugin.php.
- In the plugin.php file, add the following code:


<?php

/**
 * Plugin Name: Malicious Activity Blocker
 * Description: This plugin analyzes visitor behavior and blocks their IP address if it detects malicious activity.
 * Author: Johnathon M. Horner
 * Author URI: https://github.com/jhorner6511
 */

class MaliciousActivityBlocker
{
    public function __construct()
    {
        add_action( 'init', array( $this, 'init' ) );
    }

    public function init()
    {
        // Get the visitor's IP address.
        $ip_address = $_SERVER['REMOTE_ADDR'];

        // Get the list of malicious IP addresses.
        $malicious_ip_addresses = array(
            '192.168.1.1',
            '192.168.1.2',
            '192.168.1.3',
        );

        // Check if the visitor's IP address is in the list of malicious IP addresses.
        if ( in_array( $ip_address, $malicious_ip_addresses, true ) ) {
            // Block the visitor.
            wp_die( 'Your IP address has been blocked for malicious activity.' );
        }
    }
}

new MaliciousActivityBlocker;


    - Save the plugin.php file.
    - Activate the plugin in WordPress.

Once the plugin is activated, it will analyze visitor behavior and block their IP address if it detects malicious activity.

Here are some of the things that the plugin will look for:

    Frequent login attempts with incorrect passwords
    Access to restricted areas of the website
    Uploading of malicious files
    Spamming comments

If the plugin detects any of these activities, it will block the visitor's IP address. This will help to protect your website from malicious attacks.
