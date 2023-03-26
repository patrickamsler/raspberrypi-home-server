# SSH

## SSH Key Authentication

To login to a Raspberry Pi with SSH without a password, you can use SSH key authentication. Here are the steps to set it up:

1. Generate an SSH key pair on your local machine using the following command:
```bash
ssh-keygen
```
2. Press enter to accept the default file locations and enter a passphrase for your key (or leave it blank for no passphrase).
3. Copy your public key to the Raspberry Pi using the following command:
```bash
ssh-copy-id <username>@<ip_address>
```
Replace `<username>` with the username you want to use to login to the Raspberry Pi (usually it is default user named `pi`) and `<ip_address>` with the IP address of the Raspberry Pi on your network.

4. Enter your password when prompted.
5. You should now be able to SSH into Raspberry Pi without being prompted for a password.
```bash
ssh <username>@<ip_address>
```


