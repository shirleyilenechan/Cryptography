# Encrypting Data with OpenSSL

In this activity, you'll use the command-line tool OpenSSL to encrypt data with the AES symmetric cipher.

## Instructions

Before you start, create a new directory called `~/.openssl`. You'll save your keys, passphrases, etc., into this directory.

    mkdir ~/.openssl 

### Generating Key and IV

- generate a Key and IV using openssl 

  openssl enc -nosalt -aes-256-cbc -k <your password here> -P > ~/.openssl/key_and_iv
  
### Encryption

- Create a file called `SecretMessage.txt`, and store a message inside of it. Encrypt the file with open ssl, using th AES-256 cipher. Output the encrypted message to `SecretMessage.txt.enc`, base-64 encoded:

  openssl enc -nosalt -aes-256-cbc -in SecretMessage.txt -out SecretMessage.txt.enc -base64 -K <key> -iv <iv>

### Decryption

- Decrypt the file

  openssl enc -nosalt -aes-256-cbc -d -in SecretMessage.txt.enc -base64 -K <key> -iv <iv>
  
## Extension

- After successfully encrypting/decrypting a file, send your seat partner an encrypted message; your key; and your IV. 

- **Warning**: This is _not_ a secure practice in general, as it exposes your (secret!) key to the Terminal. This is fine for our purposes in class, but isn't recommended in production systems.

## Questions

- In order for your partner to decrypt your message, you need to send them your symmetric key. How did you do this?

    We sent the message, symmetric key, and iv via Slack 

- Was the channel you used to transfer your symmetric key secure?
    
    No, Slack is not a secure channel for exchanging keys 

- Can you think of a way to _safely_ trade symmetric keys, where "safely" means "there's no chance any eavesdropper could have stolen it"?

    Asymmetric encryption, where the symmetric key can only be decrypted with the reciever's private key. 

- What is "base64"? What do you suppose the `-base64` flag does?

    Character encoding, used to represent binary data as printable text
