# terraform-nat-module
This repo contains terraform modules ready-to-use in production

#### NAT Module

If terraform workspace == "prod" creates NAT Gateways
If workspace not equals "prod", then module creates NAT Instances for each subnet

## Usage

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

