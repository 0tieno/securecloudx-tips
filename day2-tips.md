# Day 2 Tips: 🔒 Azure Firewall Proof of Concept Lab — Step-by-Step

## Overview of What We'll Do:
![diagram-export-4-23-2025-9_47_58-AM](https://github.com/user-attachments/assets/5e133988-89b9-4596-aeb1-0f8300ec475a)

- ✅ Create Resource Group & Virtual Network
- ✅ Create Subnets (VM, Firewall, Firewall Management)
- ✅ Create Public IP
- ✅ Deploy Azure Firewall
- ✅ Deploy a Test VM
- ✅ Configure NSG
- ✅ Create Firewall Rules (DNAT + Outbound)
- ✅ Test access (RDP, outbound internet)


## 🛠️ Common Issues & Fixes
### Can’t SSH?

- Double-check DNAT and NSG rules
- Verify VM has no public IP
- Use correct key or password

### No Internet?

- Is 0.0.0.0/0 routing to firewall?
- Did you allow TCP 80/443 outbound on firewall?
- DNS might be the issue → use nslookup

### Firewall Deployment Fails?
```bash
"LinkedAccessCheckFailed"
```

- You need Network Contributor role on the subnet/resource group

## Debug Tips

- Effective Routes: On VM NIC, confirm next hop is the firewall
- Effective Rules: Make sure NSG isn't blocking needed traffic
- Use Azure Network Watcher to troubleshoot connections

## Pro Tips

- Use Azure Bastion as an alternative to SSH
- Clean up easily:

  ```bash
  az group delete --name Lab-RG --yes
  ```

- Tag your resources for easy management
- Monitor with Azure Monitor or Log Analytics

## Conclusion
You've now built a secure Azure lab with:

- NSGs for basic security
- Azure Firewall for advanced filtering
- Custom routing and NAT rules

💡 Bonus Tips

- ✅ Use Azure Bastion as a backup connection method if SSH fails
- ✅ Tag each resource (Lab, Firewall, etc.) so you don’t delete wrong ones
- ✅ Review Activity Log in the Azure portal if a deployment fails
- ✅ Use Network Watcher > Connection Troubleshoot to test VM-to-internet reachability

1. Refer to this walkthrough video if stuck: [video](https://youtu.be/m1LQmlcoUIM)
2. Refer to this step by step blog if stuck:  [blog](https://securecloudwithronney.hashnode.dev/azure-vm-security-lab-using-nsgs-and-azure-firewall-beginner-friendly-guide)


