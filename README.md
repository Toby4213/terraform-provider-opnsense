# Terraform provider for OPNSense

This is a Terraform provider that lets you:
- provision DHCP static mappings on OPNSense instance
- provision UnboundDNS host overrides

What is *NOT* in scope:

* To support every other feature than OPNSense supports

## Getting Started

In your `main.tf` file, specify the version you want to use:

```hcl
terraform {
  required_providers {
    opnsense = {
      source = "gxben/opnsense"
    }
  }
}

provider "opnsense" {
  # Configuration options
}
```

And now run terraform init:

```
$ terraform init
```

### Provider configuration

```hcl
provider "opnsense" {
  uri      = "https://acme.com"
  user     = "terraform"
  password = "complex_password"
}
```

### Resource configuration

```hcl
resource "opnsense_dhcp_static_map" "dhcp1" {
  interface = "opt3"
  mac       = "00:11:22:33:44:55"
  ipaddr    = "192.168.0.100"
  hostname  = "my_hostname"
}

resource "opnsense_dns_host_override" "dns1" {
  type   = "A"
  host   = "www"
  domain = "acme.local"
  ip     = "192.168.0.1"
}
```

## Authors

* Benjamin Zores <benjamin.zores@gmail.com>

## License

* Apache 2.0, See LICENSE file
