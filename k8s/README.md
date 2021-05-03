# Kubernetes Cluster

## Infrastructure as Code with Ansible

## Objective
Building Kubernetes Cluster using KOPS and enabling Metric Server & Cluster AutoScaler, creating infrastructure to launch RDS instance and perform VPC peering between RDS network and Kubernetes Cluster  

### Maintainer
<table>
    <thead>
      <tr>
        <th>Name</th>
        <th>NUID</th>
      </tr>
    </thead>
    <tbody>
        <tr>
            <td>Naresh Agrawal</td>
            <td>001054600</td>
        </tr>
    </tbody>
</table>

### Technology Stack
* AWS
* Ansible
* Helm

### Prerequisites
* AWS CLI
* Ansible
* Helm

###  Kubernetes Cluster
#### Build Instructions 
- Run following commands in the root directory
```
 $ ansible-playbook -i hosts setup_cluster.yml -v --extra-var "NAME=<Cluster_name>  state_store=<S3_bucket_URL> dns_zone=<DNS_Zone> compute_node_count=<Node_Count> compute_node_size=<Node_Instance_Size> clusterAutoscaler_releaseName=clusterautoscaler"
```
<b>Note</b>: Change variables value according to need 

#### Destroy Instruction 
```
 $ ansible-playbook terminate_cluster.yml --extra-var "NAME=<Cluster_name>  state_store=<S3_bucket_URL> dns_zone=<DNS_Zone> compute_node_count=<Node_Count> compute_node_size=<Node_Instance_Size> clusterAutoscaler_releaseName=clusterautoscaler"
```

###  Launch RDS Instance
#### Build Instructions 
- Run following commands in the root directory
```
 $ ansible-playbook -i hosts rds_launch.yml --extra-var "vpc_cidr=<VPC_CIDR> subnet_cidr_1=<Subnet1_CIDR> subnet_cidr_2=<Subnet2_CIDR> rds_username=<RDS_User_Name> rds_password=<RDS_Password> k8s_vpc_name=<k8s_vpc_name>"
```
<b>Note</b>: Change variables value according to need 

#### Destroy Instruction 
```
 $ ansible-playbook rds_terminate.yml --extra-var "vpc_cidr=<VPC_CIDR> subnet_cidr_1=<Subnet1_CIDR> subnet_cidr_2=<Subnet2_CIDR> rds_username=<RDS_User_Name> rds_password=<RDS_Password> k8s_vpc_name=<k8s_vpc_name>"
```

###  VPC Peering
#### Build Instructions 
- Run following commands in the root directory
```
 $ ansible-playbook -i hosts vpcPeering_setup.yml --extra-var "cluster_name=<cluster_name>"
```
<b>Note</b>: Change variables value according to need 

#### Destroy Instruction 
```
 $ ansible-playbook vpcPeering_terminate.yml --extra-var "cluster_name=<cluster_name>"
```
