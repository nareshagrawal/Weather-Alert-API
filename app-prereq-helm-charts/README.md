# App-prereq-helm-charts

## Objective
Configuring and deploying Nginx Ingress Controller(getting SSL certificate from Let's Encrypt), K8S Dashboard, EFK Stack, Prometheus and Grafana on Kubernetes Cluster using Helm Chart 

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
* Kubernetes
* Helm chart            

### Prerequisites
* Kubernetes Cluster
* Helm


### Build Instructions
 Run following commands in the root directory
```
 $ ansible-playbook -i hosts app-prereq.yml --extra-var "grafanaPassword=<Grafana_Password> webapp_domain=<API_Domain> zone_id=<Hosted_Zone_ID>"
```
<b>Note</b>: Change variables value according to need in values.yaml
