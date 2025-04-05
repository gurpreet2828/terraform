### Step 1: Installation of terraform

**Install Terraform (Linux -Ubuntu)**

Run the following commands

wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update && sudo apt install terraform

**Install Terraform on Windows**

Download from the following link 

https://developer.hashicorp.com/terraform/install

create folder named Terraform in C:\ and extract to C:\terraform

search View Advanced System Setting

go to Advanced - Environment Variables – System Variables – New

add c:\terraform

![Picture14](https://github.com/gurpreet2828/terraform/blob/main/Images/Picture14.png)

Go to cmd and type terraform –version

You will see the following screen and verify the terraform installation
 
![Picture15](https://github.com/gurpreet2828/terraform/blob/main/Images/Picture15.png)

## Step2: Install AWS CLI

**On windows**

Open CMD or Power Shell run the following command

msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi

Note: for silent install use /qn flag

**On Linux**

To install the AWS CLI, run the following command

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

unzip awscliv2.zip

sudo ./aws/install

Run the following command to check if AWS CLI is installed correctly:

aws –version

You see the following output
 
![Picture16](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture16.png)

### Step3: Create AWS account

After Creating

Click on account name - Select Security Credentials
 
![Picture17](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture17.png)

Click Create access key.
 
![Picture18](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture18.png)

Note: Download the key file or copy the Access Key ID & Secret Access Key (Secret Key is shown only once!).

### Step 4: Configure AWS CLI with the New Access Key

aws configure

It will prompt you for:

1.	AWS Access Key ID: Your access key from AWS IAM.

2.	AWS Secret Access Key: Your secret key from AWS IAM.

3.	Default region name: (e.g., us-east-1, us-west-2).

4.	Default output format: (json, table, text — default is json).

As shown bellow
 
![Picture1](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture1.png)

Check credentials added to aws configure correctly

aws sts get-caller-identity

If your AWS CLI is properly configured, you'll see a response like this:
 
![Picture2](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture2.png)

### Step 5: Install vs code

### Step 6: Install Terraform Extension in VS Code

1.	Open VS Code.

2.	Go to Extensions (Ctrl+Shift+X).

3.	Search for "HashiCorp Terraform" and click Install.

4.	Once installed, restart VS Code.
 
![Picture3](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture3.png)

Now Open Lab3-Terraform in Visual Studio Code

Launch VS Code.

Click File → Open Folder → locate the terraform code from your local machine.

Select your Terraform project directory and open it

You will see the following screen in vscode

![Picture4](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture4.png)

## Step7: Deploy EC2 instance on AWS through Terraform

Run the following commands

### 1.	Terraform init

•	terraform init is a command used in Terraform to initialize a working directory containing Terraform configuration files

•	It sets up your environment by configuring the backend, downloading necessary provider plugins, and installing modules, allowing
you to then plan, apply, and manage your infrastructure

You will see the following screen after running Terraform init

![Picture6](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture6.png) 

### 2.	Terraform validate

•	The terraform validate command checks whether your Terraform configuration is syntactically valid and internally consistent

•	Ensures your .tf files are written correctly (Syntax Checking) (valid HCL syntax)

•	Verifies references between resources are valid.

•	Does not check whether your AWS credentials or resources exist — that happens during plan and apply.
 
![Picture7](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture7.png)

### 3.	Terraform fmt

•	The terraform fmt command automatically formats your Terraform code to follow canonical style conventions.

•	Fixes indentation

•	Orders attributes consistently

•	Makes your .tf files cleaner and easier to read

•	Applies to files in the current directory by default

### 4.	Terraform plan
 
•	terraform plan is a crucial command in Terraform that allows you to preview the changes that Terraform intends to make to your infrastructure based on your current configuration and state

**Generates an Execution Plan:** Terraform produces a detailed plan outlining the proposed actions. This plan shows: 

•	Which resources will be created (+ symbol).

•	Which resources will be modified (~ symbol, showing the before and after values of changed attributes).

•	Which resources will be replaced (-/+ symbol, indicating destruction and creation).

•	Which resources will be destroyed (- symbol).

![Picture8](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture7.png)

### 5.	Terraform plan -out=ec2plan     -- ec2plan is filename you can rename according to your need

The terraform plan -out command is used to save the execution plan generated by terraform plan to a file. This is a crucial step for ensuring consistency and automation in your Terraform workflow.

![Picture9](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture9.png)

### 6.	Terraform apply

•	terraform apply is the command in Terraform that executes the actions proposed in the execution plan to create, modify, or destroy infrastructure resources. It's the command that actually makes changes to your real-world infrastructure

![Picture10](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture10.png)

Now you can access the website from browser using the URL provided in the output 

 
![Picture11](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture11.png)


### Step 8: Verifying ec2 instance running on AWS

•	Login to aws Account

•	Go to EC2 – Instances

![Picture12](https://github.com/gurpreet2828/terraform/blob/f4ef582a732d2dc6b5b9e054f7956ffd7ba9f462/Images/Picture12.png)

**Terraform destroy**

The terraform destroy command removes all resources that were created by your Terraform configuration.

**terraform plan -destroy**

for Double-checking what you're destroying!





