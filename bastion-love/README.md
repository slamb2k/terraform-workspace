This Terraform template creates a simple enterprise configuration of a Linux Bastion and Worker VM in a public and private network respectively.

![alt text](https://github.com/slamb2k/multiOneRosterAPIToSDS/blob/master/docs/nsw_high_level.png?raw=true "NSW DOE School Data Sync Process")

![alt text](bastion-love/network.png "Simple Bastion Config")

For examples of using Terraform to perform basic activites like VM creation, please refer to the [terraform-azurerm-compute GitHub repo](https://github.com/Azure/terraform-azurerm-compute "terraform-azurerm-compute GitHub repo").

This template can be executed via a local or portal hosted Azure Cloud Shell which has terraform included natively. I wanted to run it locally however in my Bash running on WSL 2. If you want to do the same, open Linux via the Windows Terminal and run through the following steps.

1. If the Azure CLI isn't installed, grab it via a single command:

   `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`

2. Check the latest version number from the [Terraform website](https://www.terraform.io/downloads.html).

3. Download the latest version (Currently 0.12.29) to the local directory.

     `wget https://releases.hashicorp.com/terraform/0.12.29/terraform_0.12.29_linux_amd64.zip`

4. Unzip the package

    `unzip terraform_0.12.29_linux_amd64.zip`

5. Move the output to the location used for public executabls

    `sudo rm /usr/local/bin/terraform -R`

6. Check the version

    `terraform --version`

As long as you have an active Azure subscription you are ready to execute this template and create all of the example resources.

1. Run `az login` to authenticate and ensure you have the correct subscription selected by executing `az account show`.

2. Clone this repo and change the current directory to the `bastion-love` folder.

3. Initialise terraform using the following command:

    `terraform init`

4. Run the plan command to see what operations will be performed when the template is applied.

    `terraform plan`

5. Execute the template by applying it:

    `terraform apply`

This template was taken from a Medium article called [Azure & Terraform — Episode 1: Building a Basic Bastion/Worker Host Virtual Network](https://medium.com/@shouldroforion/azure-terraform-part-1-building-a-basic-bastion-worker-host-virtual-network-c8bcc419cfc9). There were some deprecated settings that have been corrected so the template now works.

