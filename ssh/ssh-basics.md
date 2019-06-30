# SSH Basics
### What is SSH?
- SSH stands for 'Secure Shell'
- It is a cryptographic network protocol
  - **What is a protocol?**
    - It is way to connect between computers and have a shared agreement -- this is their protocol or language. Other kinds of protocols include HTTP (Hyper Text Transfor Protocol), HTTPS (Hyper Text Transfer Protocol Secure), FTP (File Transfer Protocol)
- Essentially, SSH is a way for machines to communicate with each other

### What makes HTTP, HTTPS, FTP, and SSH different?
- HTTP allows you to send files over the internet between browsers and servers 
- FTP allows use to send/upload files to server
- HTTPS is similar to HTTP but is encrypted. As a result, third parties cannot read the files in the communication if they intercept the messages
- SSH is another protocol allowing us to communicate between computers, allowing users to share files and modify remote computers. All data is encrypted. While HTTP/HTTPS is communication through a browser and server. SSH is communication *through a shell*
  - **What is a shell?**
    - It is a way to talk to the operating system

### What is the typical SSH format and what does it mean
- In SSH terminoloy, the **host** is the remote server and the **client** is the computer you are using to communicate with the host 
- `ssh {user}@{host}`
- `ssh` instructs the computer that you want to open an encrypted secure shell connection
- `user` is the user/account you want to access at the `host` computer(ip address or domain name) you want to be access
- After this completes, you will have a remote terminal window open
  
### What are the encryption techniques behind SSH and how do they work?
Side note: **What is encryption**? 

It is a way to hide/obscure/jumble data, making it impossible for a third party to understand or read it without some sort of decryption mechanism.
1) Symmetrical Encryption
   - Uses one secret key for encryption and decryption
     - A key from one end is used to encrypt data
     - That same key exists at the recepient end and is used to decrypt the data
     - Any part in between the sender and the recipient cannot decrypt the data because they lack the key 
     - **What is problem with this method?**
       - Anyone who posseses the key can decrypt the data being transferred
     - **How can the recipient get the key without a third party stealing it?**
       - Through a *key exchange algorithm* - a secure method to exchange keys without interception
     - **How is the key exchange algorithm secure?**
       - The keys are not actually transmitted between client and host
       - The client and host share public pieces of data, which is manipulated to independently calculate the secret key
       - So the third party may be able to get the separate public pieces of data, but it won't know the key exchange algorithm
   - The secret key is specific to *each SSH session*
   - The key is generated before client authentication
   - All packets communicated between host and client must be encypted with the secret key
2) Asymmetrical Encrytpion
   - The key exchange algorithm requires asymmmetrical encryption
   - Uses two separate keys for encryption and decryption
     - Both host and client have a public-private key pair
   - The **public key** can be shared with anyone
   - The **secret key** should ***NEVER*** be shared
   - Public keys cannot decrypt its own message
     - The public key encrypts and can be exchanged with other computers, but only the *associated private key to that exact public key* can decrypt
     - So by sharing your public key to a computer, that computer can encrypt information with that key and send information to you, which you can decrypt with your private key. 
     - A malicious third party could have your public key, but because othe **one way relationship**, there is no way for them to decrypt the packets
   - **How does this relate to SSH?**
     - Asymmetrical Encryption is **only** used in SSH during the key exchange algorithm
     - Prior to the connection between host and client, both parties generate *temporary* public and private keys
     - But once the public keys have been exchanged, **symmetric keys** are generated using the ***Difiie Hellman Key Exchange***
       - Allows the computer to use a little bit of its own private data with public data from the other system to generate an identical secret session key in private 
3) Hashing
   - As a preface: **one way hash functions** are never meant to decrypt
   - Using hashes, messages between client and host can be verified for authenticity to ensure that no third party intercepted and modified the message
   - **Hash-Based Message Authentication Codes (HMAC)**
     - The hash is generated from a combination of the symmetric key, the packet sequence number, and whatever data is inside the message
     - The MAC is sent outside the symmetrically encrypted area to the host 
   - The MAC is received by the host, but it is complete nonsense. The host has the symmetric key and the packet sequence number from the MAC, and also has the message contents via the symmetric encypted pipeline. So the host can create its own hash to make sure it matches exactly with the MAC sent by the client. If the hashes do not match, it means the message was modified somehow. 

### An overview of SSH Session
1) Secret keys are exchanged between the client and the host via asymmetric encryption 
2) Communication is then done via symmetric encryption
3) Once the connection is established, the server sends to the client a "challenge" for authorization
4) The client decrypts the "challenge" and the session begins
 