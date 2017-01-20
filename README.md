# Enhanced Networking AMI Builder
Source and packaging of ixgbevf as Amazon AMIs. Source is re-hosted from 
http://sourceforge.net/projects/e1000/files/ixgbevf%20stable/ because SourceForge is a POS and often down.
 
## Prerequisites:
All commands given below assume your system is already configured with a working installation of Packer. Instructions to
install Packer may be found at https://www.packer.io/docs/installation.html.

## Usage
### Building with Packer
To build a CentOS AMI for the default version of ixgbevf (3.2.2):

```
packer build centos.json
```

The above command assumes your system is configured with AWS Access Key ID and Secret Key in your ~/.aws/credentials
directory giving you adequate access to start/stop instances and create AMIs.

If you want to build with one of the other versions of ixgbevf that is packaged in the driver_source directory or create AMI in
a region other than the default (us-east-1), set the var options appropriately:

```
packer build -var "driver_version=2.16.4" -var "aws_region=us-west-1"  packer.json
```

### Run Scripts on your own instance
You can also run this script on any (CentOS) instance. Download the bash scripts from the scripts 
directory in this repo (or at least the *centos-install.sh* one). *centos-kernel-upgrade.sh* installs
all pending system updates, including the kernel. You should update to the latest kernel before 
building the ixgbevf driver.

To run the install, just run the *centos-install.sh* script as root, with the environment variable 
**VERSION** set.
It's easiest just to set it inline like so:

```bash
$ VERSION="3.3.2" sh centos-install.sh
```
