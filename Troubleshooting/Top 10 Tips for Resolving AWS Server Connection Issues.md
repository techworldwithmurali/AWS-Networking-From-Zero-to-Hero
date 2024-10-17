## Top 10 Tips for Resolving AWS Server Connection Issues.md

Facing AWS server connection issues? In this video, we share the top 10 tips to troubleshoot and resolve common access problems. 

1. **Check the server status:**  
   Confirm the server is running and operational.

2. **Check the Security Group (SG):**  
   Ensure port 22 (SSH) is open in the security group associated with the instance.

3. **Check NACL, Route Table, and IGW:**  
   Verify that Network ACL, route table, and Internet Gateway (IGW) settings allow traffic to reach the instance.

4. **If connecting using private IP:**  
   Ensure you're connected to a VPN (if required) to access the private IP.

5. **Verify the .pem file and permissions:**  
   Confirm you're using the correct `.pem` file and its permissions are set to `chmod 400`.

6. **If using username and password:**  
   Check that you're providing the correct credentials.

7. **Check Client VPN routes:**  
   Ensure the appropriate routes are set at the Client VPN level.

8. **Check System Logs in AWS Console:**  
   Review system and instance logs in the AWS Console for errors or issues.

9. **Reboot the server:**  
   Restart the server and verify if this resolves the issue.

10. **Still facing issues? Contact AWS Support:**  
    If the problem persists, reach out to AWS Support for further help.
