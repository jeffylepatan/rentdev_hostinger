INTRODUCTION
------------

Uses the PHPMailer library to send emails via SMTP.

For a full description of the module, visit the project page:
  http://drupal.org/project/phpmailer_smtp
To submit bug reports and feature suggestions, or to track changes:
  http://drupal.org/project/issues/phpmailer_smtp

REQUIREMENTS
------------

* Access to an SMTP server

* The Mail System module. This allows you specify different backends for
  formatting and sending e-mails
  http://www.drupal.org/project/mailsystem

* PHPMailer library 6 - installed via composer

Optional:

* To connect to an SMTP server using SSL/TLS, your PHP installation needs to
  have SSL support.

* Mime Mail module to format HTML emails
  http://www.drupal.org/project/mimemail

* Swift Mailer module to format HTML emails
  https://www.drupal.org/project/swiftmailer

INSTALLATION
------------

composer require drupal/phpmailer_smtp

CONFIGURATION
-------------

* Configure user permissions at Administer >> User management >> Access
  control >> PHPMailer SMTP module.

  Only users with the "administer phpmailer smtp settings" permission are
  allowed to access the module configuration page.

* Configure your SMTP server settings at Administer >> Configuration >>
  PHPMailer SMTP.

* Configure your Mail System settings at Administer >> Configuration >>
  Mail System.

  Select "PHPMailer SMTP" as "Sender" under "Default Mail System" and "Module-
  Specific Configuration" as required.

EXAMPLES
--------

* Using Google Mail or Google Apps as SMTP server

  To send e-mails with Google Mail use the following settings:

    SMTP server:     smtp.gmail.com
    SMTP port:       587
    Secure protocol: TLS
    Username:        your_google_mail_name@gmail.com
      or:            your_username@your_google_apps_domain.com
    Password:        your_google_mail_password

  In Advanced SMTP settings:
    Enable 'Always set "Reply-To" address' checkbox.

  Also note the sending limits for Google Mail accounts:
  http://mail.google.com/support/bin/answer.py?hl=en&answer=22839

  General instructions for Google Mail accounts:
  http://mail.google.com/support/bin/answer.py?answer=13287

* Errors when trying to send a test email

  If you see the following error messages when trying to send a test email from
  the settings page:

    SMTP -> ERROR: Failed to connect to server: Connection timed out (110)
    SMTP Error: Could not connect to SMTP host. 

  it means the mail server can not be reached, usually because your hosting
  provider is blocking the port by a firewall. The solution is to ask your
  provider to allow outgoing connections to your mail server.

* Debug settings

  PHPMailer SMTP supports rerouting all e-mails for debugging purposes, to
  prevent you from accidentally sending out e-mails to real users from a
  development site.  To enable this feature, add the following lines to the end
  of your settings.php (usually located in sites/default):

    $conf['system.maintenance']['phpmailer_smtp_debug_email']
      = 'your_debug_email@yoursite.com';

  This will change the recipient of all e-mails to the configured address.
