# RSA Encryption and Signing from the command line

### Signing Scheme

1. Hash the contents of the document using SHA256.

2. Encrypt the hash with a private RSA key. 

3. Append to the end of the file, including the newlines:

```

------------------------------------------
< ciphertext >

```
This payload is 558 bytes total (512 for the ciphertext).

### Encryption Scheme

Not yet implemented.

### Address book sctructure

By default, the address book is ~/.keys
This directory contains me/ which contains public.key and private.key.

The -genkey flag writes to me/

### Bash setup

Add `source /path/to/bashscript.sh` to your .bash_profile

### Usage

`sign -genkey` : Generates RSA key pair and writes to /path/to/addrBook/me/(private || public).key

`sign -key <key file> <infile> <outfile>` : Sign infile with temporary key. Write to outfile.

`sign -setAddrBook` : Set the address book 

`sign -getBook` : Prints address of current address book

`sign -c <file to check> < public key>` : Check signature of file with the specified pulbic key.
	--Note: `<public key>` can be a filepath or a name from the address book.

`sign -d <in> <out>` : Decrypt the in file and write to the out file.

`sign -E <public key> <in> <out>` : Sign the in file, encrypt it with the public key, write it to the out file.

`sign <in> <out>` : Sign the in file, write to the out file.

