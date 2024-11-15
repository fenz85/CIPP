---
description: Manage scheduled tenant alerts.
---

# Alerts Wizard

CIPP offers a set of scheduled, recurring alert checks. Some of these duplicate Microsoft Alerts functionality in a more MSP-friendly manner, some are not available as a Microsoft Alert at this time.

Within CIPP, there are two types of alerts.

* Scripted CIPP Alert
* Audit Log Alert

Similar to [Tenant Standards](../standards/edit-standards.md#meet-the-standards), you configure alerts using the wizard to select one or more tenants or -All Tenants- to apply alerts globally, then select from the list of available alerts.

Alert email delivers to the email address or webhook provided in CIPP settings. Alerts are delivered as an HTML-formatted table.
Audit log alerts fire once per incident.
Scripted alerts check on the interval that you define. If the condition is still present, it creates a new alert
For example, a new rule created in a mailbox does not fire an alert every time it's checked, whereas a full mailbox will keep generating alerts for as long as the condition persists.

{% hint style="info" %}
Scripted CIPP Alerts runtimes are configurable from 30 minutes to up to 1 week.
{% endhint %}

{% hint style="info" %}
Audit Log Alerts are processed in near real-time.
{% endhint %}

### Available Scripted CIPP Alerts

* Alert on users without any form of MFA
* Alert on admins without any form of MFA
* Alert on tenants without a Conditional Access policy, while having Conditional Access licensing available
* Alert on changed admin Passwords
* Alert on % mailbox quota used
* Alert on % SharePoint quota used
* Alert on licenses expiring in 30 days
* Alert on new apps in the application approval list
* Alert on Security Defaults automatic enablement
* Alert if Defender is not running (Tenant must be on-boarded in Lighthouse)
* Alert on Defender Malware found (Tenant must be on-boarded in Lighthouse)
* Alert on unused licenses
* Alert on overused licenses
* Alert on expiring application secrets
* Alert on expiring APN certificates
* Alert on expiring VPP tokens
* Alert on expiring DEP tokens
* Alert on soft deleted mailboxes

### Available Template Audit Log Alerts

* A new Inbox rule is created
* A new Inbox rule is created that forwards e-mails to the RSS feeds folder
* A new Inbox rule is created that forwards e-mails to a different email address
* A new Inbox rule is created that redirects e-mails to a different email address
* A existing Inbox rule is edited
* A existing Inbox rule is edited that forwards e-mails to the RSS feeds folder
* A existing Inbox rule is edited that forwards e-mails to a different email address
* A existing Inbox rule is edited that redirects e-mails to a different email address
* A user has been added to an admin role
* A user sessions have been revoked
* A users MFA has been disabled
* A user has been removed from a role
* A user password has been reset
* A user has logged in from a location not in the input list
* A service principal has been created
* A service principal has been removed
* A user has logged in a using a known VPN, Proxy, Or anonymizer
* A user has logged in a using a known hosting provider IP

### Example Usage
You might want to be alerted when a particular account logs into one of your tenants. For example Global Admins or break glass accounts. This is relatively simple if you have consistent naming across your tenants i.e. mylovelybreakglassaccount@tentantdomains.com

* Create an Audit log alert
* In the tenant selector, select All Tenants
* Select Azure AD as the log source
* Select "Operation" as the When property
* Select "Equals To" as the is property
* In the unput field select "A user logged in"
* Add an extra set of variables
* Select "Username" as the When property
* Select Like as the is property
* Enter the username to test for across all tenants i.e. mylovelybreakglassaccount@* (Note the * after the @ to match all domains)
* Choose the action(s) you want and save the alert.

### Feature Requests / Ideas

Please raise any [feature requests](https://github.com/KelvinTegelaar/CIPP/issues/new?assignees=\&labels=enhancement%2Cno-priority\&projects=\&template=feature.yml\&title=%5BFeature+Request%5D%3A+) on GitHub.
