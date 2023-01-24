# <p align="center"> CyberSecurity Project </p>
### <p align="center"> Brute force attack on a router through SSH </p>


## Abstract
In this paper, we present a cybersecurity project that aims to demonstrate the vulnerability of routers to brute-force attacks via SSH. We have developed a Python script that utilizes the paramiko SSHClient module and a list of commonly used passwords to attempt to gain access to a router. The results of our experimentation were inconclusive or unsuccessful, but they still reveal a vulnerability in routers and underscore the need for secure password policies and regular security updates. This project serves as a cautionary reminder to both individuals and organizations to be vigilant in protecting their networks from unauthorized access.

## Introduction
Secure Shell (SSH) is a widely used protocol for secure network communications and remote access to servers, routers and other network devices. SSH uses a combination of public-key and symmetric-key encryption to provide a secure and authenticated connection between two parties[1].

One of the most common methods used by attackers to gain unauthorized access to a device or server using SSH is a brute force attack. A brute force attack is a method of trying multiple combinations of username and password until a correct combination is found. This method can be automated using a script or program, making it possible to try thousands or even millions of possible combinations in a relatively short amount of time. While brute-force techniques have been used in codebreaking for centuries, some of the earliest documented instances of modern brute force attacks were described in a 1977 paper by renowned cryptologists Whitfield Diffie and Martin Hellman. They described how a brute force attack could be used to break a code by trying all possible keys until the correct one is found. This insight was a significant contribution to the field of cryptography and it's still relevant today as many encryption and authentication methods are still based on the same principle[9].

The history of SSH dates back to the late 1990s when the protocol was first developed by Tatu Ylönen, a researcher at the Helsinki University of Technology in Finland[1]. The original purpose of SSH was to provide a secure way of remotely accessing Unix-based systems, as the previous methods of remote access, such as Telnet, transmitted data in plaintext, making them vulnerable to eavesdropping and tampering[2].

In the early 2000s, SSH became widely adopted as the de facto standard for secure remote access to servers and network devices. The increasing popularity of SSH also led to the development of various tools and techniques for cracking the protocol's authentication mechanisms. One of the most notable examples is the development of the " SSH-cracking" program, which uses a brute force method to try different combinations of usernames and passwords[2].

As the usage of SSH grew, so did the number of vulnerabilities found in its implementation. In order to address these issues, the SSH protocol has been updated several times over the years. The most notable update is the introduction of SSH version 2 in 2006, which addresses several security issues found in version 1 and also added new features such as improved authentication and encryption methods[2].

Despite the ongoing effort to improve the security of SSH, the protocol remains vulnerable to brute force attacks. This is because SSH servers typically allow a large number of login attempts before locking or disabling the account, making it possible for an attacker to try a large number of possible combinations before being detected. However, it's worth noting that this vulnerability is not inherent to the SSH protocol itself, but rather it may arise from limitations in its implementation on certain servers, such as limited attempts and ghost rate limiting.


## Method
The methods section of this paper describes the technical details of the Python script that was developed to perform the brute force attack on the router. The specific router that was tested in this study was the Cisco WS-C3850 Wireless Controller. The script uses the Paramiko library, which is a Python implementation of the SSH protocol. The script includes the following key components:

Importing the necessary modules: The script starts by importing the Paramiko library, as well as the sys, os and termcolor modules. These modules are used for various purposes such as handling command-line arguments, working with the file system, and printing coloured text to the console[4][5][6].

Defining the ssh_connect function: This function is used to connect to the router using SSH and a specified password. The function starts by creating an instance of the Paramiko SSHClient class, which is used to handle the SSH connection[8]. The function then sets the missing host key policy to automatically add the host key and then attempts to connect to the router using the specified host, port, and password. If the connection is successful, the script prints a message indicating that the password has been found and sets the stop_flag variable to 1. If the connection fails, the script prints a message indicating that the password is incorrect.

Reading the input file: The script prompts the user to enter the target address of the router and the path to the file containing the list of passwords. The script then checks if the specified file exists, and if it does not, the script exits with an error message.

Starting the threaded SSH Bruteforce: The script then starts the threaded SSH Bruteforce on the target address using the account specified by the user. The script uses the threading module to create a new thread for each password in the input file and the time.sleep() function to pause the script for 1 second before trying the next password. The script continues to run until the stop_flag variable is set to 1, indicating that the correct password has been found or all the possible passwords have been exhausted.

In summary, the script uses the Paramiko library to perform a brute-force attack on a router by repeatedly attempting to connect to the router using a combination of host, port, and password. The script uses a list of commonly used passwords and checks if the connection is successful and if so, stops the attack and prints the successful password. For the full code please check the GitHub page at https://github.com/paul-linked/SSH-bruteforce-attack-Cybersecurity-Project.

## Results
The results of this project demonstrate the vulnerability of routers to brute-force attacks via SSH. The Python script developed for this project, which utilizes the Paramiko SSHClient module and a list of one million commonly used passwords, was run for around 10-15 hours and probably went through half a million passwords but was unable to successfully connect to the router. This indicates that the router may have a more complex password or security measures in place to prevent unauthorized access.

It is worth noting that the script is not able to determine if the login attempts were blocked due to a security measure or because the correct password was not found in the input file. One potential security measure that could be in place is ghost rate limiting, where the router will stop accepting login attempts after a certain number of failed attempts. This would prevent the script from determining if the login attempts were blocked due to a security measure or simply because the correct password was not found in the input file. To account for this, a more advanced script could include a feedback system that would indicate if the login attempts are being declined by the router due to ghost rate limiting.

This result highlights the importance of implementing strong and unique passwords to protect routers from unauthorized access. Additionally, security measures such as limiting the number of login attempts and regularly updating the router's firmware to patch known vulnerabilities can also help to protect against brute force attacks.


## Conclusion
In conclusion, this paper presented a cybersecurity project that aimed to demonstrate the vulnerability of routers to brute force attacks via SSH. The project developed a Python script that utilizes the Paramiko SSHClient module and a list of commonly used passwords to attempt to gain access to a router. The results of the experimentation indicate that the script was unable to successfully connect to the router, which could be due to the use of a complex password or security measures in place.

Future work on this project could include developing a more advanced script that can detect ghost rate limiting, or using multiple login usernames and IP addresses to bypass security measures. Additionally, running the script on a server or fast computer would make the brute force cracking and multithreading of the script a lot faster. This would not only increase the effectiveness of the script but also make it more efficient in detecting vulnerabilities in routers. Furthermore, it would be beneficial to test the script against different router models and configurations to better understand the extent of vulnerability in different types of routers and to explore methods to defend against such attacks.

The study highlights the importance of implementing strong and unique passwords to protect routers from unauthorized access. Additionally, security measures such as limiting the number of login attempts and regularly updating the router's firmware to patch known vulnerabilities can also help to protect against brute force attacks. The results of this project serve as a cautionary reminder to both individuals and organizations to be vigilant in protecting their networks from unauthorized access by implementing secure password policies and regularly updating their network devices.

In summary, this project demonstrates that routers are vulnerable to brute force attacks via SSH and highlights the importance of implementing strong and unique passwords, as well as security measures such as limiting the number of login attempts and regularly updating the router's firmware to protect against such attacks. The script developed in this project was unable to successfully connect to the router, which could be due to the use of a complex password or security measures in place.


> [1]Ylönen, T. (1995). SSH - Secure Login Connections over the Internet. Retrieved from https://www.usenix.org/conference/6th-usenix-security-symposium/ssh-secure-login-connections-over-internet

> [2]SSH Communications Security. (2021). SSH Protocol Architecture. Retrieved from https://www.ssh.com/ssh/protocol/

> [3]Paramiko. (2021). Paramiko 2.7.2 documentation. Retrieved from https://docs.paramiko.org/en/stable/

> [4]Python Software Foundation. (2021). sys — System-specific parameters and functions. Retrieved from https://docs.python.org/3/library/sys.html

> [5]Python Software Foundation. (2021). os — Miscellaneous operating system interfaces. Retrieved from https://docs.python.org/3/library/os.html

> [6]Ioffe, G. (2021). termcolor 1.1.0 documentation. Retrieved from https://pypi.org/project/termcolor/

> [7]National Institute of Standards and Technology. (2019). NIST Special Publication 800-63B. Retrieved from https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf

> [8]“Welcome to Paramiko!.” Welcome to Paramiko! - Paramiko Documentation, http://www.paramiko.org/

> [9]ExtraHop. (n.d.). Brute Force Attacks: Understanding the Basics. Retrieved from https://www.extrahop.com/resources/attacks/brute-force/





