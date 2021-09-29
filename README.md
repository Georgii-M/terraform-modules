# terraform-nat-module
This repo contains terraform modules ready-to-use in production

#### NAT Module

If terraform workspace == "prod" creates NAT Gateways
If workspace not equals "prod", then module creates NAT Instances for each subnet

## Usage

Example
```
module "nat" {
  source   = "Georgii-M/module/nat"
  version = "0.0.1"
  for_each = var.subnets

  ami                    = var.nat_ami["arm"]
  instance_type          = "t4g.nano"
  subnet_id              = aws_subnet.public[each.key].id
  vpc_security_group_ids = aws_security_group.nat_sg.*.id
  key_name               = var.ssh_keys[terraform.workspace]
  priv_route_table       = aws_route_table.private[each.key].id
}
```

##### If NAT gateway

`subnet_id = []`  
`priv_route_table = []`

##### If NAT instance

`subnet_id = []`  
`priv_route_table = []`
`ami = []`
`instance_type = []`
`vpc_security_group_ids = []`
`key_name = []`

