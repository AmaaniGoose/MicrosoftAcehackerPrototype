# Microsoft Acehacker Prototype

This repository contains code for my solution prototype built as part of Microsoft's Cybersecurity Engage program in conjunction with Acehacker

The code is fully annotated and documented. A brief description of the functioning of the code shall be given here: 

1. Cryptographically securing control messages: 

Name of file: Cryptography for control messages.ipynb 
File type: Jupyter Notebook 

This prototype implements an element of cryptography in the communication between the PLC and the controller. Two methods of cryptographically verifying the integrity of the file are implemented: 
    
The first being a straightforward symmetric key based authentication implemented with the help of Fernet. This method can be used to generate unique keys for each message sent via the secure channel. 

The second method is using a SHA-512 cryptographic hash to verify the file integrity of a message containing a secret. The hash with the message + secret is transmitted but the secret itself never sees the communication channel. On the receiver end, the secret is available to the receiver. Consequently, the receiver adds the secret to the transmitted message, computes its hash and checks with the hash transmitted. If both are equal, then successful authentication has been done.

2. Driver Change Detection using hashing: 

Name of file: Driver Change Manager.ipynb
File type: Jupyter Notebook

The second prototype patrols critical areas of the machine and determines if there have been any suspicious changes. Typically, changes only occur if there are critical bugs in the ICS. Drivers are a popular infection vector due to their relative obscurity and inherent trust in certificates published by vendors. Therefore, any unauthorized changes in the driver directory are immediately detected and the user is alerted. 

In this case, the driver folder in question is a test folder named drivers_test containing only 1 file named driver.txt

To test this file, one can start the program in Driver Change Manager.ipynb, make some minor edits and save the driver.txt file. 
It will be observed that the execution halts and an alert is generated. 
