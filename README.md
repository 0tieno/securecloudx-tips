# 🔒 Securing an Azure Deployment - capstone project
## 📌 Real-World Scenario

You are a cloud security engineer tasked with securing a new Azure deployment for a large healthcare provider. The company handles sensitive patient data and is required to comply with strict privacy regulations. Your job is to implement a comprehensive security posture across identity, network, and data layers to ensure confidentiality, integrity, and availability.

This guide will walk you through the process of **securing an Azure Virtual Machine (VM)** step by step.

---

## 📍 Table of Content
- [📌 Real-World Scenario](#-real-world-scenario)p Guide](#-securing-an-azure-deployment---step-by-step-guide)
  - [📌 Real-World Scenario](#-real-world-scenario)
  - [📍 Table of Content](#-table-of-content)
   - [🔹 How to Deploy a Secure VM](#-how-to-deploy-a-secure-vm)y-a-secure-virtual-machine)
- [🛂 Step 2: Configure Identity & Access Management](#-step-2-configure-identity--access-management)
   - [🔹 Configure RBAC](#-configure-rbac)ess Management](#-step-2-configure-identity--access-management)
   - [🔹 Enable Multi-Factor Authentication (MFA)](#-enable-multi-factor-authentication-mfa)
    - [🔹 Enable Multi-Factor Authentication (MFA)](#-enable-multi-factor-authentication-mfa)
   - [📌 Step 3.1: Deploy an Azure Firewall](#-step-31-deploy-an-azure-firewall)
   - [📌 Step 3.2: Enable DDoS Protection](#-step-32-enable-ddos-protection)ewall)
   - [📌 Step 3.3: Protect Data with Azure Key Vault](#-step-33-protect-data-with-azure-key-vault)
      - [🔹 Create a Key Vault](#-create-a-key-vault)lt](#-step-33-protect-data-with-azure-key-vault)
      - [🔹 Store a Secret in Key Vault](#-store-a-secret-in-key-vault)
      - [🔹 Retrieve the Secret in a Script](#-retrieve-the-secret-in-a-script)
- [🔍 Step 4: Enable Security Monitoring](#-step-4-enable-security-monitoring)      - [🔹 Retrieve the Secret in a Script](#-retrieve-the-secret-in-a-script)
- [🔬 Step 5: Test & Validate Security](#-step-5-test--validate-security)
- [📤 Step 6: Submit Your Work](#-step-6-submit-your-work)---

---
A **Virtual Machine (VM)** is like a computer running in the cloud. We will **deploy a secure VM** and protect it from unauthorized access.

## 🛠 Step 1: Deploy a Secure Virtual Machine

A **Virtual Machine (VM)** is like a computer running in the cloud. We will **deploy a secure VM** and protect it from unauthorized access.
azure.com).

### 🔹 How to Deploy a Secure VMVirtual Machines"** >

**"Create"**.
1. **Log in to Azure Portal**: Go to [Azure Portal](https://portal.azure.com).
2. **Create a VM**: Click on **"Virtual Machines"** > **"Create"**.
3. **Choose the configuration**:e.
    - **Subscription**: Select your Azure subscription. (e.g., `SecureVM`).
    - **Resource Group**: Create a new one or use an existing one.
    - **VM Name**: Give it a meaningful name (e.g., `SecureVM`).
    - **Region**: Select the nearest region.ze (`Standard_B2s` for testing).
    - **Image**: Choose `Windows Server 2022` or `Ubuntu 22.04`.
    - **Size**: Select a basic size (`Standard_B2s` for testing). "admin" or "root").
4. **Set up Admin Credentials**:ssword or SSH key.
    - **Username**: Choose a secure admin name (avoid "admin" or "root").
    - **Password**: Use a strong password or SSH key.
5. **Configure Network Security**:
    - **Allow SSH (Linux) or RDP (Windows) only if needed**.6. **Review & Deploy**: Click **"Review + Create"**, then **"Create"**.
    - **Attach a Network Security Group (NSG)** to control access.
6. **Review & Deploy**: Click **"Review + Create"**, then **"Create"**.✅ **Success Check**: Your secure VM is now running!

✅ **Success Check**: Your secure VM is now running!---

---
To **prevent unauthorized access**, we will set up **Role-Based Access Control (RBAC)** and **Multi-Factor Authentication (MFA)**.
## 🛂 Step 2: Configure Identity & Access Management
To **prevent unauthorized access**, we will set up **Role-Based Access Control (RBAC)** and **Multi-Factor Authentication (MFA)**.
RBAC ensures **users only have access to what they need**.
### 🔹 Configure RBAC
RBAC ensures **users only have access to what they need**.
control (IAM)**.
1. Go to **Azure Portal** > **Virtual Machines**.
2. Click on your **VM** > **Access control (IAM)**.
3. Click **"Add role assignment"**.pecific users or groups** (avoid giving full access to everyone).
4. Choose **"Virtual Machine Administrator Login"**.6. Click **Save**.
5. Select **only specific users or groups** (avoid giving full access to everyone).
6. Click **Save**.✅ **Success Check**: Only assigned users can manage the VM.

✅ **Success Check**: Only assigned users can manage the VM.
MFA requires an **extra verification step** when logging in.
### 🔹 Enable Multi-Factor Authentication (MFA)
MFA requires an **extra verification step** when logging in.*.

1. Go to **Azure Active Directory** > **Security** > **MFA**.3. Users must now verify login via **SMS, email, or an authenticator app**.
2. Click **Users**, then **Enable MFA** for required users.
3. Users must now verify login via **SMS, email, or an authenticator app**.✅ **Success Check**: Users will need a second step to log in.

✅ **Success Check**: Users will need a second step to log in.---

---## 🛡 Step 3: Secure Network and Data

## 🛡 Step 3: Secure Network and Data
A firewall **blocks unauthorized access** to the network.
### 📌 Step 3.1: Deploy an Azure Firewall
A firewall **blocks unauthorized access** to the network.r **"Firewall"**.

1. In **Azure Portal**, search for **"Firewall"**.
2. Click **"Create a Firewall"**.r **Private** IP.
3. Select the **Resource Group** and enter a **Firewall Name**.5. Click **"Review + Create"**, then **"Create"**.
4. Under **Network settings**, select **Public** or **Private** IP.
5. Click **"Review + Create"**, then **"Create"**.✅ **Success Check**: Firewall is active and filtering traffic.

✅ **Success Check**: Firewall is active and filtering traffic.---

---
A **Distributed Denial of Service (DDoS) attack** floods a network with traffic, causing downtime.
### 📌 Step 3.2: Enable DDoS Protection
A **Distributed Denial of Service (DDoS) attack** floods a network with traffic, causing downtime.

1. In **Azure Portal**, go to **"Networking"**.3. Attach it to the **Resource Group** containing your VM.
2. Select **DDoS Protection** > **Enable DDoS Standard**.
3. Attach it to the **Resource Group** containing your VM.✅ **Success Check**: DDoS protection is enabled.

✅ **Success Check**: DDoS protection is enabled.---

---
Instead of storing **passwords or API keys** in code, we use **Azure Key Vault**.
### 📌 Step 3.3: Protect Data with Azure Key Vault
Instead of storing **passwords or API keys** in code, we use **Azure Key Vault**.

#### 🔹 Create a Key Vaultfor **"Key Vault"** and click **"Create"**.
1. Go to [Azure Portal](https://portal.azure.com).
2. Search for **"Key Vault"** and click **"Create"**.
3. Choose:- `MySecureVault`.
    - **Resource Group**: Same as your VM.
    - **Key Vault Name**: Example - `MySecureVault`.4. Click **"Review + Create"**, then **"Create"**.
    - **Region**: Same as your VM.
4. Click **"Review + Create"**, then **"Create"**.
*Key Vault** > Click **Secrets** > **Generate/Import**.
#### 🔹 Store a Secret in Key Vault
1. Open **Key Vault** > Click **Secrets** > **Generate/Import**.
2. Enter:uperSecretPassword123!`
    - **Name**: `DatabasePassword`3. Click **Create**.
    - **Value**: `MySuperSecretPassword123!`
3. Click **Create**.ecret in a Script
Using Azure CLI**
#### 🔹 Retrieve the Secret in a Script
**Using Azure CLI**
```shkeyvault secret show --name DatabasePassword --vault-name MySecureVault
az login
az keyvault secret show --name DatabasePassword --vault-name MySecureVaultUsing poweshell**
```
tSecret -VaultName "MySecureVault" -Name "DatabasePassword"
**Using PowerShell**cret.SecretValueText
```powershell```
$secret = Get-AzKeyVaultSecret -VaultName "MySecureVault" -Name "DatabasePassword"
$secret.SecretValueText✅ Success Check: Your app can securely retrieve the secret!
```

✅ **Success Check**: Your app can securely retrieve the secret!To detect threats, enable Azure Security Center and Azure Sentinel.

---Go to Security Center and enable recommendations.

## 🔍 Step 4: Enable Security MonitoringEnable Azure Sentinel for real-time monitoring.
To detect threats, enable Azure Security Center and Azure Sentinel.
Configure alerts for security events.
1. Go to **Security Center** and enable recommendations.
2. Enable **Azure Sentinel** for real-time monitoring.✅ Success Check: Security alerts are active.
3. Configure alerts for security events.

✅ **Success Check**: Security alerts are active.
Try accessing the VM without assigned RBAC permissions (should fail).
---
Simulate unauthorized access attempts (should trigger alerts).
## 🔬 Step 5: Test & Validate Security
1. Try accessing the VM without assigned RBAC permissions (should fail).Verify DDoS protection and firewall rules.
2. Simulate unauthorized access attempts (should trigger alerts).
3. Verify DDoS protection and firewall rules.✅ Success Check: Security measures work as expected.

✅ **Success Check**: Security measures work as expected.
✅ Overview
---ion Steps

## 📤 Step 6: Submit Your Work✅ Testing & Validation
Upload a report with:
- ✅ OverviewSubmit via: Microsoft Forms
- ✅ Implementation Steps
- ✅ Screenshots
- ✅ Testing & Validation

Submit via: **Microsoft Forms**

---

🚀 Congratulations! You have successfully secured an Azure deployment! 🎉 Congratulations! You have successfully secured an Azure deployment! 🎉
*
