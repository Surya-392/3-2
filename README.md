# 3-2
🔹 STEP 1: Check Security Group
Go to EC2 → Security Groups → Inbound rules
Ensure this rule exists:
Type: SSH
Port: 22
Source: My IP
❌ If SSH is blocked → connection will fail

🔹 STEP 2: Open PuTTY
1.Launch PuTTY
2.In Session screen:
Host Name (or IP address): EC2—CONNECT—COPY (DNS NAME)
ubuntu@<PUBLIC-IP>
Example:
ubuntu@3.110.xxx.xxx

🔹 STEP 3: Attach the .ppk Key
In PuTTY left menu, go to:
Connection → SSH → Auth → Credentials
1.Click Browse
2.Select your .ppk file
3.Click Open

🔹 STEP 4: Connect to EC2
Click Open
First time → click Yes (security alert)
PuTTY will log in automatically as:
ubuntu
🎉 You are now connected to your Ubuntu EC2 instance

🧪 VERIFY CONNECTION
Run:
whoami
Output should be:
Ubuntu


 Connect EC2 Ubuntu Instance Using PuTTY (Windows) ---USING PEM KEYPAIR

PREREQUISITES
You must have:
✅ EC2 Ubuntu instance running
✅ Public IPv4 address (or Elastic IP)
✅ Key pair (.pem file) used while launching EC2
✅ PuTTY & PuTTYgen installed
👉 Download PuTTY:
https://www.putty.org

🔹 STEP 1: Convert .pem to .ppk using PuTTYgen
PuTTY cannot use .pem directly.
Steps:
1.Open PuTTYgen
2.Click Load
3.Select your .pem file
(change file type to All Files)
4.Click Open
5.Click Save private key
6.Save as keyname.ppk
✔ Conversion done

🔹 STEP 2: Get EC2 Public IP
Go to:
AWS Console → EC2 → Instances---CONNECT –COPY DNS NAME

🔹 STEP 3: Configure PuTTY
1️⃣ Open PuTTY
Session:
Host Name (or IP address): dns name

2️⃣ Load Private Key
Go to:
Connection → SSH → Auth → Credentials
Click Browse
Select your .ppk file

🔹 STEP 4: Connect
Click Open
First time → click Yes (security alert)
Login happens automatically as:
ubuntu
🎉 You are now connected to Ubuntu EC2

🧪 VERIFY CONNECTION
Run:
whoami
Output:
ubuntu

):

Connecting to EC2 Using AWS CloudShell
1.Create the EC2 instance using a key pair (.pem).
2.Log in to AWS Console and click on the CloudShell icon (terminal icon on the top-right).
3.Once CloudShell opens, go to AWS Services → EC2.
4.Select your EC2 instance and click Connect.
5.Choose the SSH client tab.
6.Copy the ssh -i command shown there.
7.Paste the command in CloudShell and try to run it.
❌ It will fail with an error like:
“key pair is not available / no such file or directory”
(because the key file is not yet in CloudShell).
8.Now, in CloudShell, click on the “+” (Actions) icon on the right side.
9.Select Upload file and upload the key pair (.pem) from your local machine.
10.After upload, copy the ssh -i command again from EC2 → Connect → SSH client.
11.Paste and execute the command in CloudShell.
12.✅ You are now successfully connected to the EC2 instance.

Step-by-Step: Create Windows EC2 Instance and Connect via RDP
Step 1: Launch a Windows EC2 Instance
1.Log in to your AWS Management Console.
2.Navigate to EC2 → Instances → Launch Instances.
3.Select an Amazon Machine Image (AMI):
oChoose a Windows Server AMI (e.g., Windows Server 2019 or 2022).
4.Choose an Instance Type (e.g., t2.micro for free tier or as per your requirement).
5.Configure Instance Details as needed.
6.Add Storage if required (default is usually sufficient).
7.Configure Security Group:
oEnsure RDP port 3389 is allowed.
oSource can be My IP (for security) or a wider range if needed.
8.Select or create a new Key Pair:
oDownload the .pem file (keep it safe; it’s needed to decrypt the password).
9.Click Launch Instance.

Step 2: Get the Public DNS / IP
1.After the instance is running, go to EC2 → Instances.
2.Select your instance and note the Public DNS (IPv4) or Public IP.

Step 3: Retrieve the Windows Administrator Password
1.Select your instance → Click Connect → RDP Client.
2.Click Get Password.
3.Upload your Key Pair (.pem) file.
4.Click Decrypt Password.
5.Copy the Administrator password shown.

Step 4: Connect via RDP
1.On your local Windows machine, open Remote Desktop Connection (mstsc).
2.In the Computer field, enter the Public DNS or IP address of the EC2 instance.
3.Click Connect.
4.In the login prompt:
oUsername: Administrator
oPassword: Paste the decrypted password from Step 3.
5.Click OK.

Step 5: You’re connected
Your Windows EC2 instance desktop should appear.
You can now use it as a normal Windows machine.
