# Weeks-7-8-Project-WordPress-vs.-Kali
For this week's assignment, discover and demonstrate similar proofs-of-concept for at least an additional three and (up to five) exploits affecting an older version of WP. For each exploit, provide the following information in the README.md:

• A small writeup indicating the steps you used to recreate

• The types / classes of vulnerabilities involved and any related CVE identifiers

• Identify affected versions and patches

• Links to the source code, where possible

• A screen cap

CVE 2017-5611:

This is an SQL injection vulnerability in Wordpress version 4.7.1. This vulnerability allows remote hackers to execute arbitrary commands by taking advantage an affected plugin or theme that mishandles a crafted post type name. This vulnerability requires very little knowledge or skill to exploit and is ranked 7.5 on the Common Vulnerability Scoring System. Authentication is not required to exploit the vulnerability. Modification of files and information on the system is possible, but the scope of what the attacker can affect is limited. The CWE ID is 89. Example of this is found at https://github.com/WordPress/WordPress/commit/85384297a60900004e27e417eac56d24267054cb)

CVE 2017-5492:

This is a cross-site request forgery CSRF vulnerability in the widget-editing accesibility-mode feature in Wordpress version 4.7.1. This allows remote hackers to hijack the authentication of unspcified victims for requestst that allow for widget-access action that is related to wp-aadmin/includes/class-wp-screen.php. This vulnerability has a CVSS score of 6.8. This vulnerability allows for limited scope of modification on the attacker’s behalf. Authenticcation is not required to exploit this vulnerability.

Example of this is found at https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733

CVE-2016-5836 This vulnerability allows remote attackers to cause a denial of service attack via unspecified vendors due to the oEmbed protocol implementation in the WordPress. This vulnerability existed in Wordpress version 4.5.2 and was secured in the 4.5.3 version. This has a CVSS score of 5.0 and was considered to be a low level of access complexity, meaning that very little knowledge is needed to exploit this. The CWE is not defined for this vulnerability.
