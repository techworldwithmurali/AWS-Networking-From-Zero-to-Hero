### Establishing SSH Access with Password Authentication on Linux

#### Step 1: Create the User
1. **Log in to the server** (if you have another access method).
2. **Create the user `murali`** with the following command:
   ```bash
   sudo adduser murali
   ```
3. **Set a password** for the user:
   ```bash
   sudo passwd murali
   ```

#### Step 2: Configure SSH for Password Authentication
1. **Edit the SSH configuration file**:
   ```bash
   sudo nano /etc/ssh/sshd_config
   ```
   - Look for the line that says `#PasswordAuthentication yes` and uncomment it (remove the `#`).
   - Ensure it reads:
     ```plaintext
     PasswordAuthentication yes
     ```

#### Step 3: Restart the SSH Service
1. **Restart the SSH daemon** to apply the changes:
   ```bash
   sudo systemctl restart sshd
   ```
   - On some systems, you may need to use `sudo service ssh restart`.

#### Step 4: Connect to the Server
1. Use the following command to connect:
   ```bash
   ssh murali@52.65.85.65
   ```
   - Replace `52.65.85.65` with your server's actual IP address.

2. **Enter the password** for the `murali` user when prompted.

### Additional Tips
- **Security Note**: Using password authentication can pose security risks. Consider using SSH keys for better security.
- **Firewall Rules**: Ensure your firewall allows SSH connections on port 22 or the port you've configured.
- **Check SSH Status**: If you're having trouble, check the SSH service status with:
  ```bash
  sudo systemctl status sshd
  ```
