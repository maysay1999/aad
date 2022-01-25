# Cloud Manager Connector Setup: Procedure

Reference:\
[Set up permissions for your Azure account](https://docs.netapp.com/us-en/occm/task_creating_connectors_azure.html)\
[Azure credentials and permissions](https://docs.netapp.com/us-en/occm/concept_accounts_azure.html)\


### Diagram
[View hands-on diagram](https://github.com/maysay1999/aad/blob/main/cvo/220117_hands-on_diagram_cvo.pdf)

## Option 1: Create the Connector with your Azure account

## 1. Edit "Policy_for_Setup_As_Service_Azure.json"
- After "AssignableScopes", add "/subscriptions/{your_subscription}"

```bash
"AssignableScopes": [
"/subscriptions/d333af45-0d07-4154-943d-c25fbzzzFAKE"
],
```

## 2. Upload json file and execute "az role definition create" command

- Upload the json file on Azure Cloud Shell
- Create a new role named "Azure SetupAsService": `az role definition create --role-definition Policy_for_Setup_As_Service_Azure.json`

## 3. Edit "Policy_for_cloud_Manager_Azure_3.9.12.json"
- After "AssignableScopes", add "/subscriptions/{your_subscription}"

```bash
"AssignableScopes": [
"/subscriptions/d333af45-0d07-4154-943d-c25fbzzzFAKE"
],
```

## 2. Upload json file and execute "az role definition create" command

- Upload the json file on Azure Cloud Shell
- Create a new role named "Azure SetupAsService": `az role definition create --role-definition Policy_for_cloud_Manager_Azure_3.9.12.json`


## 3. Add role assigment under subscription
- Subscriptions
- Access control (IAM)
- Add > Add role assignment and select **Azure SetupAsService** role
- User, group, or service principal 
- Select members, choose **your user account**
- Review + assign

## 4. Have acccess with [Cloud Manager website](https://cloudmanager.netapp.com/) and click "Connector"
![Click Connector](https://github.com/maysay1999/aad/blob/main/cvo/images/click_connector.jpg)

## 5. Choose Azure
![Choose azure](https://github.com/maysay1999/aad/blob/main/cvo/images/choose_azure.jpg)

## 6. Setups of authentication
- User Name: ConnectorAdmin
![authentication](https://github.com/maysay1999/aad/blob/main/cvo/images/authentication.jpg)

## 7. Details setups
- Connector Instance Name: Connector01
- Connector Role: Cloud Manager Operator
![details](https://github.com/maysay1999/aad/blob/main/cvo/images/details.jpg)

## 8. Configure Network
- VNet: NetApp-Vnet
- Subnet: FrontEnd
- Public IP: Enable
![Network](https://github.com/maysay1999/aad/blob/main/cvo/images/network.jpg)

## 9. Security Group
- HTTP: My IP
- HTTPS: My IP
- SSH: My IP
![nsg](https://github.com/maysay1999/aad/blob/main/cvo/images/nsg.jpg)

---