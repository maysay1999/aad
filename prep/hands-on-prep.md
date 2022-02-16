# Preparation for Azure NetApp Files Hands-on Session

## Prerequisites

- Register provider

```Bash
az provider register --namespace Microsoft.NetApp
```

- Activate Share AD

```Bash
az feature register --namespace Microsoft.NetApp --name ANFSharedAD
```

- Activate Dynamic tier change

```Bash
az feature register --namespace Microsoft.NetApp --name ANFTierChange
```

- Activate Unix permission

```Bash
az feature register --namespace Microsoft.NetApp --name ANFUnixPermissions
```

- Activate Unix chown

```Bash
az feature register --namespace Microsoft.NetApp --name ANFChownMode
```

- Activate Restore individual files

```Bash
az feature register --namespace Microsoft.NetApp --name ANFSingleFileSnapshotRestore
```

To verify

```Bash
az feature list --namespace Microsoft.NetApp -o table
```

Warning) ANF does NOT support **Free subscription**, **Visual Studio subscriber**, **MSDN platform** and **Microsoft Partner Network subscribers** by default.  To activate ANF, Service Request shall be raised.  Please refer to [this site](https://docs.microsoft.com/en-us/azure/azure-netapp-files/request-region-access). 

### **Network Diagram**

[Network diagram of Hands-on Seesion ANF NFS](https://github.com/maysay1999/aad/blob/main/prep/images/220203_hands-on_diagram_linux_nfs_auseast.pdf)

[Network diagram of Hands-on Seesion ANF SMB](https://github.com/maysay1999/aad/blob/main/prep/images/220203_hands-on_diagram_smb_japaneast.pdf)

[Cross Region Replication (DR)](https://github.com/maysay1999/aad/blob/main/prep/images/220107_crr_diagram.pdf)

## SMB option

[Network diagram of Hands-on Seesion ANF SMB](https://github.com/maysay1999/aad/blob/main/prep/images/220203_hands-on_diagram_smb_japaneast.pdf)

## 1. Create Resouce Group of ADDS (Domain Controller)

```Bash
az group create -n anfdemo-rg -l japaneast
```

## 2. Create Windows 2019 VM and promote primary domain controller

* Have access to this URL: [ARM of Create a domain contoller](https://github.com/Azure/AzureStack-QuickStart-Templates/tree/master/active-directory-new-domain)

Note) It takes over 20 mins.

## 3. Testing of ANF account creation

Insert this line on Cloud Shell

```Bash
az netappfiles account create -g anfdemo-rg -n anftest -l japaneast`
```

## 4. Registration for new features

* SMB CA: [SMB CA](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR2Qj2eZL0mZPv1iKUrDGvc9UQUFTUjExUDA5VU5KMUY1RllSVjNEOUVTWCQlQCN0PWcu)

* ANF Backup: [ANF Backup](https://forms.office.com/pages/responsepage.aspx?id=v4j5cvGGr0GRqy180BHbR2Qj2eZL0mZPv1iKUrDGvc9UMkI3NUIxVkVEVkdJMko3WllQMVRNMTdEWSQlQCN0PWcu)

---
