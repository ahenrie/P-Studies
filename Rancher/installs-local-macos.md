# Dependencies

1. Install Rancher Desktop: `https://rancherdesktop.io/`
2. Install helm (macos): `brew install helm`
3. For Jetstack charts: `helm repo add jetstack https://charts.jetstack.io`
4. Create cert-manager namespace: `kubectl create namespace cert-manager`
5. Install cert-manager service: `helm install cert-manager jetstack/cert-manager --namespace cert-manager --version v1.10.2 --set installCRDs=true`

## Install Rancher
1. `helm repo add rancher-latest https://releases.rancher.com/server-charts/latest`
2. Create cattle-system namespace: `kubectl create namespace cattle-system`
3. Install Rancher application: `helm install rancher rancher-latest/rancher --namespace cattle-system --set hostname=your.host.name --set bootstrapPassword=password --wait --timeout=10m`
