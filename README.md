# sqlinjection
Exploiting SQL Injection vulnerability

# AIM:
To exploit SQL Injection vulnerability using Multidae web application in Metasploitable2

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode


### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

SQL Injection is a sort of infusion assault that makes it conceivable to execute malicious SQL statements. These statements control a database server behind a web application. Assailants can utilize SQL Injection vulnerabilities to sidestep application safety efforts. They can circumvent authentication and authorization of a page or web application and recover the content of the whole SQL database. 
Identify IP address using ifconfig in Metasploitable2
#OUTPUT

Use the above ip address to access the apache webserver of Metasploitable2 from kali/parrot linux. In Kali Linux use the ip address in a web browser.
##  OUTPUT


Select Multidae from the menu listed as shown above. The page is displayed as below:
##  OUTPUT
<img width="728" height="412" alt="e8 1" src="https://github.com/user-attachments/assets/d52061d4-89f2-463c-b3d2-0173ec876bd0" />



Click on the menu Login/Register and register for an account
##  OUTPUT

<img width="997" height="907" alt="e8 2" src="https://github.com/user-attachments/assets/0ac69534-8391-467f-8dd1-2b59e094cc20" />


Click on the link “Please register here”
##  OUTPUT
<img width="995" height="917" alt="e8 3" src="https://github.com/user-attachments/assets/1f897cbf-b510-4c33-b648-38e7aad24fbb" />



Click on “Create Account” to display the following page:
##  OUTPUT
<img width="992" height="917" alt="e8 4" src="https://github.com/user-attachments/assets/bd5c64c9-da60-4124-b128-7cb59c7f8a82" />


The login structure we will use in our examples is straightforward. It contains two input fields (username and password), which are both vulnerable. The back-end content creates a query to approve the username and secret key given by the client. Here is an outline of the page rationale:


($query = “SELECT * FROM users WHERE username=’$_POST[username]’ AND password=’$_POST[password]’“;).
 For the username put “ganesh” or “anything” and for the password put (anything’ or ‘1’=’1) or (admin’ or ‘1’=’1) then try to log in, and you’ll be presented with an admin login page.
##  OUTPUT

<img width="997" height="901" alt="e8 5" src="https://github.com/user-attachments/assets/3eac78ac-5501-4253-81d0-9b572d36d7b6" />


Click “Login”. The logged in page will show as below:
##  OUTPUT

<img width="992" height="925" alt="e8 6" src="https://github.com/user-attachments/assets/367a879b-11da-4eca-953b-7cf93f8735d4" />


If error faced in registration follow the following steps in metasploitable 2:


This issue is caused by a misconfiguration in the config.inc located in the /var/www/mutillidae folder on Metasploitable 2 VM.

Edit config.inc
Edit config.inc file located in /var/www/mutillidae folder on Metasploitable 2 by typing the following commands [one at the time]:
cd /
sudo nano /var/www/mutillidae/config.inc
Type msfadmin when prompted for the root password. 
Once nano opens config.inc file, look for the line $dbname = ‘metasploit’ as shown in Figure  below:
##  OUTPUT

<img width="995" height="912" alt="e8 7" src="https://github.com/user-attachments/assets/d60983c9-179b-49a2-8f52-56ce1cc1aac2" />

Replace ‘metasploit’ with ‘owasp10’ and make sure the lines end with semicolon ; as shown in Figure
##  OUTPUT


<img width="999" height="920" alt="e8 8" src="https://github.com/user-attachments/assets/c0ef6e99-f891-4471-83ce-299017a6feff" />


Save and exit the config.inc
Save than exit the config.inc file by typing CTRL+X keys on your keyboard and the Y [Enter] when prompted to save the file
Restart the Apache server
To restart Apache, type the following command in the terminal. Alternatively, you can just reboot Metasploitalbe 2 VM.
sudo /etc/init.d/apache2 reload
##  OUTPUT


<img width="989" height="918" alt="e8 9" src="https://github.com/user-attachments/assets/7ba67991-6471-42be-b1cb-87c30d001479" />


# Reset Mutillidae database
Refresh the page then clicking on the Reset DB menu option to reset the Mutillidae database [Figure ]. Click OK when prompted.
##  OUTPUT

<img width="996" height="918" alt="e8 10" src="https://github.com/user-attachments/assets/ceb29acc-bbbb-477d-ae84-b44c217e7b51" />




# Test the new configuration
Alright. Now is time to test if we managed to fix the database issue. Go ahead and register a new account on the Mutillidae webpage.

 The Mutillidae database error no longer appears 
#OUTPUT

<img width="1000" height="920" alt="e8 11" src="https://github.com/user-attachments/assets/ca30ad47-dee8-46cc-bb2d-ee21363cef9e" />


Now after logging out you will see the login page. In the login page give ganesh’ # (myusername). You can see the page now enters into the administrator page as before when giving the password.
#OUTPUT
<img width="1001" height="917" alt="e8 12" src="https://github.com/user-attachments/assets/2399faa7-7682-4dbb-9149-36a18d40e8b5" />


Click the login button and you will see it enter into the administrator page.
#OUTPUT

<img width="1001" height="918" alt="e8 13" src="https://github.com/user-attachments/assets/7e5c76e3-5b0d-4d8e-bf3b-ad269ea33743" />


## Union-based SQL injection

UNION-based SQL injection assaults enable the analyzer to extract data from the database effectively. Since the “UNION” operator must be utilized if the two inquiries have precisely the same structure, the attacker must craft a “SELECT” statement like the first inquiry. 
we will be using the “User Info” page from Mutillidae to perform a Union-Based SQL injection attack. Go to “OWASP Top 10/A1 — Injection/SQLi — Extract-Data/User Info” 

After logging out, Now choose the menu as shown below:
##  OUTPUT

<img width="1007" height="922" alt="e8 14" src="https://github.com/user-attachments/assets/b24c2c17-8bf4-4309-94ae-e8bc73f80e3b" />


From this point, all our attack vectors will be performed in the URL section of the page using the Union-Based technique.There are two different ways to discover how many columns are selected by the original query. The first is to infuse an “ORDER BY” statement indicating a column number. Given the column number specified is higher than the number of columns in the “SELECT” statement, an error will be returned.

## RESULT:
The SQL Injection vulnerability is successfully exploited using the Multidae web application in Metasploitable2.
