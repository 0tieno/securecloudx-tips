# Quick Tips for Day 1

1. **Think of IAM like a security guard** – It controls **who** gets in and **what** they can do.  
2. **Microsoft Entra ID (Azure AD) = Identity Provider** – It manages users, groups, and authentication.  
3. **RBAC = Access Control** – Assign roles like "Reader" or "Admin" to limit actions.  
4. **MFA (Multi-Factor Authentication) = Extra Security** – Even if someone steals your password, they still need a second verification (e.g., a phone code).  
5. **Least Privilege Principle** – Always give users the lowest level of access they need to do their job.  

## Common Challenges & How to Solve Them  

#### ❌ Challenge 1: **Can't Assign RBAC Roles**  
**Problem:** You don’t see the option to assign roles in the Azure portal.  
✔ **Solution:**  
- Ensure you have **Owner** or **User Access Administrator** permissions.  
- Go to **Azure Portal → Subscription → IAM (Access Control) → Role Assignments** and check your role.  

### ❌ Challenge 2: **MFA Not Prompting on Login**  
**Problem:** Users are still logging in without MFA.  
✔ **Solution:**  
- Check if MFA is **enabled for all users** in **Azure AD Security > Conditional Access**.  
- If using Conditional Access, ensure MFA is **applied to the correct group**.  

### ❌ Challenge 3: **Accidentally Locked Out**  
**Problem:** You enabled strict MFA and lost access.  
✔ **Solution:**  
- Use an **emergency access account** (excluded from MFA).  
- If locked out, reset your settings using **Azure Support**.  

### ❌ Challenge 4: **Users Still Have Too Much Access**  
**Problem:** A user can still edit or delete resources despite applying RBAC.  
✔ **Solution:**  
- Check for **role inheritance**—if a user is in multiple groups, they might inherit higher privileges.  
- Use **Azure Role Assignments** to check their exact permissions.  

### ❌ Challenge 5: **Can't Test VM Access Restrictions**  
**Problem:** The test user can still log in without restrictions.  
✔ **Solution:**  
- Verify that the test user **does not belong to an admin role**.  
- Check if RBAC settings **propagated properly** (sometimes changes take a few minutes).   

## Challenge Yourself  
🔹 Can you set up **a new user** and assign them the **"Reader" role** in Azure?  
🔹 Can you enable **MFA** for an account and test logging in?  
🔹 Try **removing access** for a user and see what happens when they try to log in!  

IAM is **your first line of defense** in cloud security! Proper identity and access controls help **prevent unauthorized access, data breaches, and cyber threats**.🔐
