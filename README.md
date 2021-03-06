[![Build Status](https://dev.azure.com/doncanton/Ansible%20LAMP/_apis/build/status/Better-Computing-Consulting.azure-devops-ci-ansible-lamp-deployment?branchName=master)](https://dev.azure.com/doncanton/Ansible%20LAMP/_build/latest?definitionId=44&branchName=master)
# azure-devops-ci-ansible-lamp-deployment
Automatic deployment of cloud infrastructure and LAMP application stack using Ansible and Azure DevOps CI

* logon to https://dev.azure.com/

* Create DevOps project

* Create Service Connection of the type Azure Resource Manager using "Service Principal (manual)" with the same name as in azure-pipelines.yml line 17. Use the following Azure CLI commands to get the information for the Service Connection:
   * __az account subscription list__ (for subscription id and name)
   * __az account show__ (for tenantid)
   * __az ad sp create-for-rbac --name your-sp-name__ (for Service Principal Id [appid] and Service Principal Key [password])

* Create a Pipeline pointing to your clone of this repository and save it.

* At a git prompt run __git commit --allow-empty -m "trigger ci"__ and __git push origin master__ to trigger the Azure DevOps Pipeline CI and deploy the cloud infrastructure and LAMP application stack.

During the execution of the playbooks you can follow the changes on Azure with CLI command for example, 
* az vm list
* az network nsg list
* az network nsg rule list
* az network public-ip list

After initial deployment you can further customize the infrastructure or the LAMP stack by commiting your changes to the code.

There is a blog that explains with details some aspects of the playblooks, such as how ssh key authentication is handled and how the LAMP playbooks are executed from within the new Azure infrastructure.

https://bcc.bz/post/azure-devops-ci-ansible-lamp-deployment 

There is also a video that shows the execution of the entire process and deploying an update by re-triggering the pipeline.

https://youtu.be/Vlt3Zgk8jKQ


:smiley:
