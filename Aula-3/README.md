# Comandos terraform
terraform init <br>
terraform fmt -recursive <br>
terraform plan -out="tfplan.out" <br>
terraform validate <br>
terraform apply -auto-approve <br>
terraform destroy <br>

### Atenção: version utilizado na criação do cluster
Podemos ter o erro abaixo:

" Error: Error creating Kubernetes cluster: 
```
POST https://api.digitalocean.com/v2/kubernetes/clusters: 422 (request "b2b70a8b-9a74-440f-a775-419786dd5287") failed to test requested version slug "1.23.9.do-0" for VersionFeatureDockerVpcBugFixed feature: invalid version slug
│
│   with digitalocean_kubernetes_cluster.k8s-iniciativa,
│   on main.tf line 14, in resource "digitalocean_kubernetes_cluster" "k8s-iniciativa":
│   14: resource "digitalocean_kubernetes_cluster" "k8s-iniciativa" 
```

Utilizando a versão desta forma é possível fazer o apply:
"resource "digitalocean_kubernetes_cluster" "k8s-iniciativa" {
  name    = var.k8s_name
  region  = var.region
  version = "1.22.12-do.0"

  node_pool {
    name       = "default"
    size       = "s-2vcpu-4gb"
    node_count = 2
  }
}"