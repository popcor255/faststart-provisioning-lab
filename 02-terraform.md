# Part 2 - Terraform

## Provision dev tools with scripts

### Look at the provided terraform modules

The automated scripts have been provided in two parts - 1) a set of reusable, pluggable modules and 2) a set of "stages"
that put those modules together to set up an environment.

1. Clone the terraform modules repo - https://github.com/ibm-garage-cloud/garage-terraform-modules
2. Take a look through the way the modules are organized
3. Look at the structure of one module, e.g. https://github.com/ibm-garage-cloud/garage-terraform-modules/tree/master/generic/cluster/namespaces

Each module has the same basic structure:
- Module input variables are defined in `variables.tf`
- Module output variables are defined in `outputs.tf`
- Module logic is defined in `main.tf`
  
### Setup the terraform scripts

For the purposes of the lab and for the sake of time, a stripped down version of the `iteration-zero` repository has been
created that installs a subset of the basic components. It requires a little bit of setup before the scripts can be run
to allow the script to access the cluster.

1. Clone the faststart iteration-zero repo - https://github.com/ibm-garage-cloud/iteration-zero-faststart
2. Copy `credentials.template` into a file named `credentials.properties`
3. In `credentials.properties`, replace {IBMCLOUD_API_KEY} with the APIKEY from the top of the box note
4. Open `terraform/settings/environment.tfvars". Set the 'cluster_name' and the 'resource_group_name' to 
match the cluster you've been assigned

### Run the terraform scripts

Once the scripts are configured, they can be executed. A docker image is provided that sets up the tools required for the
scripts to run.

1. Start the docker image to create the CLI environment by running `./launch.sh`. You should see an IBM Cloud banner
2. Kick off the process by running `./runTerraform.sh`. You will see a screen that confirms the settings that will be applied. Select Y
3. The script will prompt for the dev_namespace. Provide the value used above (e.g. user01-dev)
4. In about 5 minutes the process will complete (note: the tools may not be available yet)
5. Open the OpenShift console to look at the deployments and pods in your namespace

