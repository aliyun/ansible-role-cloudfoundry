#The repository aims to provide some template that can be used to deploy CloudFoundary quickly.

Prepare
=======
1. Install ansible

       $ sudo pip install ansible
2. Install terraform
   * Download terraform and terraform-provider-alicloud and unarchive them

         $ wget https://releases.hashicorp.com/terraform/0.10.0/terraform_0.10.0_linux_amd64.zip
         $ unzip terraform_0.10.0_linux_amd64.zip
         $ wget -qO- https://github.com/alibaba/terraform-provider/releases/download/V1.2.6/terraform-provider-alicloud_darwin-amd64.tgz | tar -xzvf -

   * Build a work directory, such as /root/work/terraform

         $ mkdir -p /root/work/terraform

   * Copy terraform package to above directory

         $ mv ./terraform /root/work/terraform/
         $ mv ./bin/terraform-provider-alicloud /root/work/terraform/
   * Set PATH

         $ export PATH="/root/work/terraform:$PATH"

   ~> **NOTE:** Above terraform packages only support MAC OS.
   For more packages, refer to [terraform](https://releases.hashicorp.com/terraform/?_ga=2.10495730.736095916.1505112587-366911210.1497366445)
   and [terraform-provider-alicloud](https://github.com/alibaba/terraform-provider/releases).


Usage
=====
Execute the following command with Alicloud Access Key and Region ID:

    $ ansible-playbook -i hosts deploy.yml --extra-vars "alicloud_access_key=XXXXXX alicloud_secret_key=XXXXXX alicloud_region=cn-beijing" -c paramiko

`NOTE`: If you want to delete Alicloud resources, you can set parameter `delete` to `true` in above command.



"Finding deployments:", "  Director responded with non-successful status code '401' response 'Not authorized: '/deployments'", "'", "Exit code 1"]