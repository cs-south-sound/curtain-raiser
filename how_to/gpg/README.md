# GPG

> GNU Privacy Guard

> Transmit confidential encrypted project information between collaborators.

## Procedure

1. On the command line confirm availability of gpg

   ```bash
   gpg --version
   ```

2. Generate an RSA key, size 4096, valid for 1 year, with your real name and email address, and a
passphrase known only to you. ([4](https://dev.to/nerdynene/extensive-guide-to-gnu-privacy-guard-gpg-2a11#generate-gpg-key-pair))

   ```bash
   gpg --full-generate-key
   ```

3. List keys in the keyring

   ```bash
   gpg --list-keys
   ```

   * The long-keyid is the low 64 bits, or last 16 hex digits, of the fingerprint.
   * The short-keyid is the low 32 bits, or last 8 hex digits, of the fingerprint.

4. Export key to a file for sharing

   ```bash
   gpg --export -a key-id > myfullname-public-key.asc
   ```

   See the contents of the key file

   ```bash
   cat myfullname-public-key.asc
   ```

   This public key file can now be attached to an email for sharing with your collaborators.

5. Importing a public key received from a corresponding collaborator, ie by email, or other sharing method.

   ```bash
   gpg --import collaborator-fullname-public-key.asc
   ```

6. Encrypt a message with your long-key-id

   ```bash
   gpg -r long-key-id -a -e a-confidential-message.txt
   # OR your email, but not both
   gpg -r myemail@url -a -e a-confidential-message.txt
   ```

   * attach the message to an email or share another way

7. Decrypt a message with the senders public key-id, and then
   save to a file.  GPG will automatically search the keyring
   for the matching public key.

   ```bash
   gpg -d a-confidential-message.txt.asc > a-confidential-message-decrypted.txt
   ```

For additional key management search the following references.

## References

1. [GnuPG](https://gnupg.org/)
2. GnuPG [wikipedia](https://en.wikipedia.org/wiki/GNU_Privacy_Guard)
3. [How-to](https://www.howtogeek.com/427982/how-to-encrypt-and-decrypt-files-with-gpg-on-linux/)
4. [Guide](https://dev.to/nerdynene/extensive-guide-to-gnu-privacy-guard-gpg-2a11)

