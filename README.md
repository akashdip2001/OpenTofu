# OpenTofu

[<img align="right" alt="lfel1009-getting-started-with-opentofu" width="300" src="https://github.com/user-attachments/assets/76e667e7-1207-4c55-ac22-39954c148ea0">](https://www.credly.com/badges/f8f23f57-70f5-4193-a939-1f9bd6622b4d/public_url) 


### Brief Notes on OpenTofu  

#### **Lab 1: Installing OpenTofu**  
1. **Update System & Install Tools**:  
   ```bash
   sudo apt-get update  
   sudo apt-get install -y apt-transport-https ca-certificates curl gnupg  
   ```  

2. **Download & Execute Installation Script**:  
   ```bash
   curl -fsSL https://get.opentofu.org/install-opentofu.sh -o install-opentofu.sh  
   chmod +x install-opentofu.sh  
   sudo ./install-opentofu.sh --install-method snap  
   ```  

3. **Verify Installation**:  
   ```bash
   tofu -h  
   ```  

4. **Enable Auto-completion**:  
   ```bash
   tofu install-autocomplete  
   ```  

#### **Lab 2: Basics of OpenTofu**  
1. **Create a Resource File**:  
   - Create `main.tf`:  
     ```hcl
     resource "local_file" "hello_world" {  
       filename = "${path.module}/demo.txt"  
       content  = <<-EOF  
       Hello World!!!  
       Welcome to the fascinating world of OpenTofu!  
       EOF  
     }  
     ```  

2. **Format Code**:  
   ```bash
   tofu fmt main.tf  
   ```  

3. **Initialize Directory**:  
   ```bash
   mkdir demo && mv main.tf demo/ && cd demo  
   tofu init  
   ```  

4. **Validate and Plan**:  
   ```bash
   tofu validate  
   tofu plan  
   ```  

5. **Apply Changes**:  
   ```bash
   tofu apply  
   ```  

6. **Verify Output**:  
   ```bash
   cat demo.txt  
   ```  

7. **Cleanup Resources**:  
   ```bash
   tofu destroy  
   ```  

#### **Lab 3: Creating a Virtual Machine**  
1. **Setup AWS Credentials**:  
   - Example `main.tf`:  
     ```hcl
     provider "aws" {  
       region     = "us-east-1"  
       access_key = "your_access_key"  
       secret_key = "your_secret_key"  
     }  

     resource "aws_instance" "firstvm" {  
       ami           = "ami-053b0d53c279acc90"  
       instance_type = "t2.micro"  
       subnet_id     = "your_subnet_id"  
     }  
     ```  

2. **Initialize, Plan & Apply**:  
   ```bash
   tofu init  
   tofu plan  
   tofu apply  
   ```  

3. **Destroy Resources**:  
   ```bash
   tofu destroy  
   ```  

#### **Key Commands**  
- **Initialize Directory**: `tofu init`  
- **Validate Config**: `tofu validate`  
- **Generate Plan**: `tofu plan`  
- **Apply Plan**: `tofu apply`  
- **Destroy Resources**: `tofu destroy`  

---

### **OpenTofu: Theoretical Knowledge and Practical Guide**

#### **What is OpenTofu?**  
OpenTofu is an open-source infrastructure as code (IaC) tool used for provisioning and managing infrastructure resources in a declarative manner. It enables developers and DevOps engineers to define infrastructure configurations in human-readable files, which can then be applied consistently across different environments.

---

#### **Key Features of OpenTofu**  
1. **Declarative Configuration**:  
   Write infrastructure configurations in a simple and structured format.
   
2. **Provider Support**:  
   Supports multiple cloud providers (AWS, Azure, GCP) and on-premise solutions.

3. **State Management**:  
   Tracks the state of your infrastructure to identify changes and apply only necessary updates.

4. **Automation**:  
   Automates the creation, updating, and destruction of infrastructure.

5. **Version Control Friendly**:  
   Configuration files can be stored in version control systems like Git for collaboration and history tracking.

---

#### **Core Concepts**  

1. **Providers**:  
   Plugins that interact with cloud services or APIs (e.g., AWS, Azure).  

   Example:  
   ```hcl
   provider "aws" {
       region = "us-east-1"
   }
   ```

2. **Resources**:  
   Describes infrastructure components like servers, databases, or storage.  

   Example:  
   ```hcl
   resource "aws_instance" "my_instance" {
       ami           = "ami-053b0d53c279acc90"
       instance_type = "t2.micro"
   }
   ```

3. **State**:  
   A file that records the current state of your managed resources, ensuring consistency.

4. **Modules**:  
   Reusable blocks of configuration, similar to functions in programming.

---

#### **Workflow**  
1. **Write Configuration**:  
   Define resources and their attributes in `.tf` files.  

2. **Initialize Directory**:  
   Use `tofu init` to download necessary plugins and set up the working directory.  

3. **Plan Changes**:  
   Use `tofu plan` to preview the changes that will be made.  

4. **Apply Configuration**:  
   Use `tofu apply` to implement the changes in your infrastructure.  

5. **Destroy Resources**:  
   Use `tofu destroy` to clean up resources when no longer needed.

---

#### **Advantages of OpenTofu**  
- **Consistency**: Ensures infrastructure remains consistent across different environments.  
- **Collaboration**: Teams can collaborate using version-controlled configuration files.  
- **Scalability**: Easily manage and scale infrastructure.  
- **Efficiency**: Automates repetitive tasks, saving time and reducing human error.

---

#### **Practical Steps (Lab Examples)**

**Lab 1: Local File Resource**  
- **Goal**: Create a local file using OpenTofu.  
- **Steps**:  
  1. Define a `local_file` resource in `main.tf`.  
  2. Initialize, plan, and apply the configuration.  
  3. Verify the created file.

**Lab 2: Virtual Machine Creation**  
- **Goal**: Launch an AWS EC2 instance.  
- **Steps**:  
  1. Define AWS credentials and an EC2 resource in `main.tf`.  
  2. Initialize, plan, and apply the configuration.  
  3. Destroy resources after use.

---

#### **Best Practices**  
1. **Use Modules**: For reusable and organized configurations.  
2. **Manage State Securely**: Use remote storage (e.g., S3) for team collaboration.  
3. **Version Locking**: Lock provider versions to avoid unexpected changes.  
4. **Review Plans**: Always review `tofu plan` before applying.  
5. **Backup State Files**: Prevent accidental state loss.

---

#### **Common Commands**  
- `tofu init`: Initializes the directory and downloads provider plugins.  
- `tofu validate`: Validates the configuration for syntax errors.  
- `tofu plan`: Previews the changes to be applied.  
- `tofu apply`: Implements the changes.  
- `tofu destroy`: Deletes the resources defined in the configuration.  

---

By combining theoretical knowledge with hands-on practice and the [Exam](https://www.linkedin.com/posts/the-linux-foundation-training-%26-certification_iac-opentofu-devops-activity-7280661407161860096-SSSJ?utm_source=share&utm_medium=member_desktop), OpenTofu empowers you to efficiently manage and automate infrastructure, making it an essential tool for modern cloud and DevOps workflows.

</br>
</br>

[![akashdip-mahapatra-5971be11-a39d-4c4a-a81f-a251043206ae-certificate_page-0001](https://github.com/user-attachments/assets/52cf30f7-e0af-4ea1-a398-7ea1d54995e6)](https://www.linkedin.com/posts/akashdip2001_devops-opentofu-iac-activity-7280700253522051074-TcAb)


