# Upgrades

    $ sudo apt update -y && sudo apt upgrade -y


# Enumeration (subdomains)(username)(atthentication bypass)
# ffuf

    $ ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.54.22/customers/signup -mr "username already exists"


-w wordlists path
-u ip domain ex https://google.com
-H host
