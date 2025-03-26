# 🔒 Securing an Azure Deployment - Step-by-Step Guide

## 📌 Real-World Scenario  
Imagine you're a **Cloud Security Engineer** working for a **healthcare provider**. Your job is to **secure a new Azure deployment** to protect sensitive patient data and ensure compliance with regulations.  

This guide will walk you through the process of **securing an Azure Virtual Machine (VM)** step by step.  

---

## 📍 Table of Contents
1. [Deploy a Secure Virtual Machine](#step-1-deploy-a-secure-virtual-machine)
2. [Configure Identity & Access Management](#step-2-configure-identity--access-management)
3. [Secure Network and Data](#step-3-secure-network-and-data)
   - [Deploy an Azure Firewall](#step-31-deploy-an-azure-firewall)
   - [Enable DDoS Protection](#step-32-enable-ddos-protection)
   - [Protect Data with Azure Key Vault](#step-33-protect-data-with-azure-key-vault)
4. [Enable Security Monitoring](#step-4-enable-security-monitoring)
5. [Test & Validate Security](#step-5-test--validate-security)
6. [Submit Your Work](#step-6-submit-your-work)

---

## 🛠 Step 1: Deploy a Secure Virtual Machine
A **Virtual Machine (VM)** is like a computer running in the cloud. We will **deploy a secure VM** and protect it from unauthorized access.

### 🔹 How to Deploy a Secure VM
1. **Log in to Azure Portal**: Go to [Azure Portal](https://portal.azure.com).
2. **Create a VM**: Click on **"Virtual Machines"** > **"Create"**.
3. **Choose the configuration**:
   - **Subscription**: Select your Azure subscription.
   - **Resource Group**: Create a new one or use an existing one.
   - **VM Name**: Give it a meaningful name (e.g., `SecureVM`).
   - **Region**: Select the nearest region.
   - **Image**: Choose `Windows Server 2022` or `Ubuntu 22.04`.
   - **Size**: Select a basic size (`Standard_B2s` for testing).
4. **Set up Admin Credentials**:
   - **Username**: Choose a secure admin name (avoid "admin" or "root").
   - **Password**: Use a strong password or SSH key.
5. **Configure Network Security**:
   - **Allow SSH (Linux) or RDP (Windows) only if needed**.
   - **Attach a Network Security Group (NSG)** to control access.
6. **Review & Deploy**: Click **"Review + Create"**, then **"Create"**.

✅ **Success Check**: Your secure VM is now running!

---

## 🛂 Step 2: Configure Identity & Access Management
To **prevent unauthorized access**, we will set up **Role-Based Access Control (RBAC)** and **Multi-Factor Authentication (MFA)**.

### 🔹 Configure RBAC
RBAC ensures **users only have access to what they need**.

1. Go to **Azure Portal** > **Virtual Machines**.
2. Click on your **VM** > **Access control (IAM)**.
3. Click **"Add role assignment"**.
4. Choose **"Virtual Machine Administrator Login"**.
5. Select **only specific users or groups** (avoid giving full access to everyone).
6. Click **Save**.

✅ **Success Check**: Only assigned users can manage the VM.

### 🔹 Enable Multi-Factor Authentication (MFA)
MFA requires an **extra verification step** when logging in.

1. Go to **Azure Active Directory** > **Security** > **MFA**.
2. Click **Users**, then **Enable MFA** for required users.
3. Users must now verify login via **SMS, email, or an authenticator app**.

✅ **Success Check**: Users will need a second step to log in.

---

## 🛡 Step 3: Secure Network and Data

### 📌 Step 3.1: Deploy an Azure Firewall
A firewall **blocks unauthorized access** to the network.

1. In **Azure Portal**, search for **"Firewall"**.
2. Click **"Create a Firewall"**.
3. Select the **Resource Group** and enter a **Firewall Name**.
4. Under **Network settings**, select **Public** or **Private** IP.
5. Click **"Review + Create"**, then **"Create"**.

✅ **Success Check**: Firewall is active and filtering traffic.

---

### 📌 Step 3.2: Enable DDoS Protection
A **Distributed Denial of Service (DDoS) attack** floods a network with traffic, causing downtime.

1. In **Azure Portal**, go to **"Networking"**.
2. Select **DDoS Protection** > **Enable DDoS Standard**.
3. Attach it to the **Resource Group** containing your VM.

✅ **Success Check**: DDoS protection is enabled.

---

### 📌 Step 3.3: Protect Data with Azure Key Vault
Instead of storing **passwords or API keys** in code, we use **Azure Key Vault**.

#### 🔹 Create a Key Vault
1. Go to [Azure Portal](https://portal.azure.com).
2. Search for **"Key Vault"** and click **"Create"**.
3. Choose:
   - **Resource Group**: Same as your VM.
   - **Key Vault Name**: Example - `MySecureVault`.
   - **Region**: Same as your VM.
4. Click **"Review + Create"**, then **"Create"**.

#### 🔹 Store a Secret in Key Vault
1. Open **Key Vault** > Click **Secrets** > **Generate/Import**.
2. Enter:
   - **Name**: `DatabasePassword`
   - **Value**: `MySuperSecretPassword123!`
3. Click **Create**.

#### 🔹 Retrieve the Secret in a Script
🔹 **Using Azure CLI**
```sh
az login
az keyvault secret show --name DatabasePassword --vault-name MySecureVault
```
🔹 **Using poweshell**
```sh
$secret = Get-AzKeyVaultSecret -VaultName "MySecureVault" -Name "DatabasePassword"
$secret.SecretValueText
```

✅ Success Check: Your app can securely retrieve the secret!

🔍 Step 4: Enable Security Monitoring
To detect threats, enable Azure Security Center and Azure Sentinel.

Go to Security Center and enable recommendations.

Enable Azure Sentinel for real-time monitoring.

Configure alerts for security events.

✅ Success Check: Security alerts are active.


🔬 Step 5: Test & Validate Security
Try accessing the VM without assigned RBAC permissions (should fail).

Simulate unauthorized access attempts (should trigger alerts).

Verify DDoS protection and firewall rules.

✅ Success Check: Security measures work as expected.

📤 Step 6: Submit Your Work
Upload a report with: ✅ Overview
✅ Implementation Steps
✅ Screenshots
✅ Testing & Validation

Submit via: Microsoft Forms


🚀 Congratulations! You have successfully secured an Azure deployment! 🎉
