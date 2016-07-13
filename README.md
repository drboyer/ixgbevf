# Enhanced Networking AMI Builder
Source and packaging for ixgbevf as Amazon CentOS AMI. Source is re-hosted from 
http://sourceforge.net/projects/e1000/files/ixgbevf%20stable/ because SourceForge is a POS and often down.
 
## Prerequisites:
All commands given below assume your system is already configured with a working installation of Packer. Instructions to
install Packer may be found at https://www.packer.io/docs/installation.html.

## Usage
To build an AMI for the default version of ixgbevf (2.16.4):

```
packer build packer.json
```

The above command assumes your system is configured with AWS Access Key ID and Secret Key in your ~/.aws/credentials
directory giving you adequete access to start/stop instances and create AMIs.

If you want to build with one of the other versions of ixgbevf that is packaged in the driver_source directory set the
driver_version var appropriately:

```
packer build -var "driver_version=3.2.2" packer.json
```

