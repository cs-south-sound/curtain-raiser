# SSH-KEYGEN

> Generate keys for secure shell access to a server
> A discussion specifically for cs-south-sound projects 

## Help

The `man` command will provide some hints, 
```bash
man ssh-keygen
```
See the reference section below for an online man pages

> Note there is no command line help argument like -h that returns hints

## Create private and public keys on the client

```bash
ssh-keygen -f ~/.ssh/id_mykeyname-rsa -t rsa -b 4096 -C "myusername"
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

In the directory `~/.ssh/` expect two files named:
```bash
  * id_mykeyname-rsa      (secret - do not share it)
  * id_mykeyname-rsa.pub  (public and not secret)
```

The importance of defining a key name is the expectation to be working
on more than one server which will require separate unique keys.
Name your key something that reminds you of your project or the server.

The algorithm chosen is [rsa](https://en.wikipedia.org/wiki/RSA_(cryptosystem)) with an encryption number of bits 4096.
Examine the generated keys as follows:

```bash
cat ~/.ssh/id_mykeyname-rsa
cat ~/.ssh/id_mykeyname-rsa.pub
```

Finally note that the comment `myusername` is added to the end of the key.
It may not be necessary, but some applications may expect the username.
Additionally it may be a helpful for the server administrator to know to
whom the key belongs.

## Share the public key

> Only the public key, never the private

* With care, copy and paste is possible.  Make the screen font small enough to copy all the symbols including the start and end notes. Paste where requested.
* Submit directly to a server where you already have a password with:

  ```bash
  ssh-copy-id username@url
  #OR
  ssh-copy-id username@ipaddress 
  ```

## Reference

1. ssh.com [academy](https://www.ssh.com/academy/ssh/keygen)
2. [man7](https://www.man7.org/linux/man-pages/man1/ssh-keygen.1.html)
3. [linux.die.net](https://linux.die.net/man/1/ssh-keygen)
4. [wikipedia](https://en.wikipedia.org/wiki/Ssh-keygen)
5. example[rsa-algorithm/](https://justcryptography.com/rsa-algorithm/)
