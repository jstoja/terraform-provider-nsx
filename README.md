# Terraform-Provider-NSX

A Terraform provider for VMware NSX.  The NSX provider is used to interact
with resources supported by VMware NSX.  The provider needs to be configured
with the proper credentials before it can be used.

## Getting Started

```terra
# Configure the VMware NSX Provider
provider "nsx" {
    nsxusername = "${var.nsx_username}"
    nsxpassword = "${var.nsx_password}"
    nsxserver = "${var.nsx_server}"
}

# Create a logical switch
resource "nsx_logic_switch" "OVP_1" {
    ...
}
```

## Authentication

The NSX provider offers flexible means of providing credentials for
authentication.  The following methods are supported, in this order and
explained below:

* Static credentials
* Environment variables

### Static credentials

Static credentials can be provided by adding `nsxusername`, `nsxpassword`
and `nsxserver` in-line in the nsx provider block:

Usage:

```terra
provider "nsx" {
    nsxusername = "username"
    nsxpassword = "password"
    nsxserver = "apnsx020"
}
```

### Environment variables

You can provide your credentials via NSXUSERNAME, NSXPASSWORD and NSXSERVER
environment variables, representing your user name, password and NSX server
respectively.

```terra
provider "nsx" {}
```

Usage:

```bash
$ export NSXUSERNAME='username'
$ export NSXPASSWORD='password'
$ export NSXSERVER='apnsx020'
$ terraform plan
```
