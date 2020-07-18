# terraforming demo

This repo contains some proof-of-concept code for a demo of [terraforming](https://github.com/dtan4/terraforming).

# Usage

The terraforming project is a Ruby app. To avoid installing Ruby Gems directly with System Ruby, I use RVM:

```text
▶ rvm list
=* ruby-2.4.1 [ x86_64 ]
   ruby-2.7.0 [ x86_64 ]
```

Assuming this is set up then install terraforming using Bundler. Clone this repo, then:

```text
▶ bundle install
Fetching gem metadata from https://rubygems.org/.............
Resolving dependencies...
Fetching aws-eventstream 1.1.0
Installing aws-eventstream 1.1.0
etc
```

Then:

```text
▶ bundle show terraforming 
/Users/alexharvey/.rvm/gems/ruby-2.4.1/gems/terraforming-0.18.0
```

# Demo

Help message:

```text
▶ bundle exec terraforming help
Commands:
  terraforming alb             # ALB
  terraforming asg             # AutoScaling Group
  terraforming cwa             # CloudWatch Alarm
  terraforming dbpg            # Database Parameter Group
  terraforming dbsg            # Database Security Group
  terraforming dbsn            # Database Subnet Group
  terraforming ddb             # DynamoDB
  terraforming ec2             # EC2
  terraforming ecc             # ElastiCache Cluster
etc
```

I note that a limitation is that code generation depends on the author of this project having created a "resource" in his project matching each of the resources in Terraform. Many are unavailable. The available ones can be seen here:

https://github.com/dtan4/terraforming/tree/master/lib/terraforming/resource

# Code generate a VPC

For fun, here is how easy it is to code generate a VPC after manually creating one:

```text
▶ bundle exec terraforming vpc
resource "aws_vpc" "vpc-07a59518ae4faa320" {
    cidr_block           = "172.31.0.0/16"
    enable_dns_hostnames = true
    enable_dns_support   = true
    instance_tenancy     = "default"

    tags {
    }
}
```

That's the default VPC from my personal account.
