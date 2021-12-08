# Preparation for Azure NetApp Files Hands-on Session

### **Prerequisites**
- Register provider: `az provider register --namespace Microsoft.NetApp`
- Share AD: `az feature register --namespace Microsoft.NetApp --name ANFSharedAD`
- Dynamic tier change: `az feature register --namespace Microsoft.NetApp --name ANFTierChange`
- Unix permission: `az feature register --namespace Microsoft.NetApp --name ANFUnixPermissions`
- Unix chown: `az feature register --namespace Microsoft.NetApp --name ANFChownMode`

Warning) Free subscription, Visual Studio subscriber and Microsoft Partner Network subscribers should raise Support Request for ANF activation. 

## SMB option

## 1. Create Resouce Group of ADDS (Domain Controller)
`az group create -n anfdemo-rg -l japaneast`

## 2. Create Windows 2019 VM and promote primary domain controller
- Have access to this URL: [ARM of Create a domain contoller](https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/active-directory-new-domain)

Note) It takes over 20 mins. 

## 3. Testing of ANF account creation
Insert this line on Cloud Shell
`az netappfiles account create -g anfdemo-rg -n anftest -l japaneast`

## 4. Registration for new features
- SMB CA: [SMB CA](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2Qj2eZL0mZPv1iKUrDGvc9UQUFTUjExUDA5VU5KMUY1RllSVjNEOUVTWCQlQCN0PWcu)
- ANF Backup: [ANF Backup](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbR2Qj2eZL0mZPv1iKUrDGvc9UMkI3NUIxVkVEVkdJMko3WllQMVRNMTdEWSQlQCN0PWcu)
