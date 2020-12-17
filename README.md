Azure Bastion Host Terraform module
=====================================

[![Opstree Solutions][opstree_avatar]][opstree_homepage]

[Opstree Solutions][opstree_homepage] 

  [opstree_homepage]: https://opstree.github.io/
  [opstree_avatar]: https://img.cloudposse.com/150x150/https://github.com/opstree.png

Terraform module which creates network skeleton on AWS.

These types of resources are supported:

* [Bastion](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/bastion_host)

Terraform versions
------------------

Terraform 0.13.

Usage
------

```hcl
module "rgBastion" {
  source = "git::https://gitlab.com/ot-azure/terraform/bastion.git?ref=feature/readme"
  bastion_subnet_rg_name = module.azurerg.rgName
  bastion_subnet_vnet_name = module.azurevnet.vnet_name
  bastion_location = "eastus"
  bastion_name = "otbastion"
  bastion_rg_name = module.azurerg.rgName
  bastion_publicIp_Id = module.rgPublicIp.public_ip_id
  bastion_subnet_addr = [cidrsubnet(module.rgVnet.vnet_address[0], 8, 2)]
  bastion_tag = {
      env:"stage"
  }
}

```


Tags
----
* Tags are assigned to resources with name variable as prefix.
* Additial tags can be assigned by tags variables as defined above.

Inputs
------
| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| bastion_name | Name of the bastion host | `string` | `"otbastion"` | no |
| bastion_location | Location in which the Bastion host would be created | `string` | `"eastus"` | yes |
| bastion_tag | tag to associate with te Bastion host | `string` | `"dev"` | no |

Output
------
| Name | Description |
|------|-------------|
|op1 |value |

## Related Projects

Check out these related projects. 

### Contributors

|  [![Naveen Verma][naveen_avatar]][naveen_homepage]<br/>[Naveen Verma][naveen_homepage] |
|---|

  [naveen_homepage]: https://github.com/naveenverma023
  [naveen_avatar]: https://avatars2.githubusercontent.com/u/61639221?s=400&u=de7879e92ac9cff3d9ababff74c1b593d13302ca&v=4
