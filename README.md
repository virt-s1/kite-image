# kite-image

kite-image is one of sub-projects of kite, which is to run Linux application or kernel test on public and private cloud platform, such as VMWare ESXi, OpenStck, AWS EC2, Google Cloud Platform, Azure, etc.

kite-image will help to build public and private cloud image.

## Image Building

kite-image will build/update images for different cloud platforms weekly.

**Images**

| Cloud Platform | RHEL 8.2.z | RHEL 8.3.z | RHEL 8.4.z | RHEL 8.5.z | RHEL 8.y | RHEL 9.y |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| VMWare ESXi 7.0 | `template-rhel-8-2-bios`/`template-rhel-8-2-efi` | `template-rhel-8-3-bios`/`template-rhel-8-3-efi` | `template-rhel-8-4-bios`/`template-rhel-8-4-efi` | `template-rhel-8-5-bios`/`template-rhel-8-5-efi` | `template-rhel-8-6-bios`/`template-rhel-8-6-efi` | `template-rhel-9-0-bios`/`template-rhel-9-0-efi` |
| AWS EC2 AMI SSM (x86_64) | `kite-image-rhel-8-2-x86_64` | `kite-image-rhel-8-3-x86_64` | `kite-image-rhel-8-4-x86_64` | `kite-image-rhel-8-5-x86_64` | `kite-image-rhel-8-6-x86_64` | `kite-image-rhel-9-0-x86_64` |
| AWS EC2 AMI SSM (ARM64) | `kite-image-rhel-8-2-aarch64` | `kite-image-rhel-8-3-aarch64` | `kite-image-rhel-8-4-aarch64` | `kite-image-rhel-8-5-aarch64` | `kite-image-rhel-8-6-aarch64` | `kite-image-rhel-9-0-aarch64` |
| Openstack | `kite-image-rhel-8-2-x86_64` | `kite-image-rhel-8-3-x86_64` | `kite-image-rhel-8-4-x86_64` | `kite-image-rhel-8-5-x86_64` | `kite-image-rhel-8-6-x86_64` | `kite-image-rhel-9-0-x86_64` |
| Google Cloud Platform | `kite-image-rhel-8-2-x86-64` | `kite-image-rhel-8-3-x86-64` | `kite-image-rhel-8-4-x86-64` | `kite-image-rhel-8-5-x86-64` | `kite-image-rhel-8-6-x86-64` | `kite-image-rhel-9-0-x86-64` |
| Azure | `kite-image-rhel-8-2-x86_64` | `kite-image-rhel-8-3-x86_64` | `kite-image-rhel-8-4-x86_64` | `kite-image-rhel-8-5-x86_64` | `kite-image-rhel-8-6-x86_64` | `kite-image-rhel-9-0-x86_64` |


### Image Building

Build ESXi image with:

    ansible-playbook -v -i inventory -e cloud_platform=esxi build.yaml

Build Openstack qcow2 image with:

    ansible-playbook -v -i inventory -e cloud_platform=openstack build.yaml

Build AWS EC2 AMI image with:

    ansible-playbook -v -i inventory -e cloud_platform=aws build.yaml

Build Google Cloud Platform image with:

    ansible-playbook -v -i inventory -e cloud_platform=gcp build.yaml

Build Azure image with:

    ansible-playbook -v -i inventory -e cloud_platform=azure build.yaml

## kite-deploy configuration

You can set these environment variables to configure to run kite-image

    TEST_OS           The OS to run the tests in. Currently supported values:
                          "rhel-8-2"
                          "rhel-8-3"
                          "rhel-8-4"
                          "rhel-8-5"
                          "rhel-8-6"
                          "rhel-9-0"

    ARCH              Image architecture
                          "x86_64"
                          "aarch64"(AWS ONLY)

    VSPHERE_SERVER    The vSphere server hostname or IP address

    VSPHERE_USERNAME  Username to login vSphere server

    VSPHERE_PASSWORD  Password to login vSphere server

    ESXI_HOST         ESXi host name or IP address

    ESXI_DATACENTER   Datacenter name

    ESXI_DATASTORE    Datastore name

    ESXI_FIRMWARE     ESXi firmware, bios or efi

    OS_CLIENT_CONFIG_FILE       Absolute path of clouds.yaml for OpenStack auth

    AWS_SHARED_CREDENTIALS_FILE AWS credentials file for AWS auth

    GCP_PROJECT       Google Cloud Platform project name

    GCP_SERVICE_ACCOUNT_NAME    Google Cloud Platform service account name

    GCP_SERVICE_ACCOUNT_FILE    Google Cloud Platform service account file path

    GCP_STORAGE_BUCKET_NAME     Google Cloud Platform storage bucket name

    AZURE_CLIENT_ID             Azure principle account client id

    AZURE_SECRET                Azure principle account secret

    AZURE_SUBSCRIPTION_ID       Azure principle account subscription id

    AZURE_TENANT                Azure principle account tenant
