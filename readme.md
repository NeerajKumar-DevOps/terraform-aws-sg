#  AWS Security Group using Terraform

##  Overview

This configuration creates a reusable **AWS Security Group** using Terraform.  
It is designed to be flexible by using variables and common tagging standards.

---

##  Configuration Summary

- Creates a **Security Group inside a VPC**
- Allows **all outbound (egress) traffic**
- Uses **dynamic inputs** for name, description, and VPC
- Applies **standardized tags** for resource management

---

##  Variables

- `project_name` → Project name (default: spacex)  
- `environment` → Environment (default: dev)  
- `sg_name` → Security group name  
- `sg_description` → Security group description  
- `vpc_id` → VPC ID where SG will be created  
- `sg_tags` → Custom tags (optional)  

---

##  Locals

- `common_tags` → Standard tags:
  - Project  
  - Environment  
  - Terraform  

- `common_name_suffix` → `<project>-<environment>`  
  (used for consistent resource naming)

---

##  Resource Created

### Security Group
- Attached to given VPC  
- Name → `<project>-<environment>-<sg_name>`  
- Outbound Rule → Allow all traffic (`0.0.0.0/0`)  
