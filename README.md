# istio -k8s
# istio installtion 

1 - Download and extract istio automatically on linux

curl -L https://istio.io/downloadIstio | sh -

2 - Move to that Directory

# The installation directory contains:

A - Sample applications in samples/

B - The istioctl client binary in the bin/ directory.

3 - Add the istioctl client to your path

export PATH=$PWD/bin:$PATH

cd istio-1.20.3

pwd

export PATH=$PATH:pwd/bin

for example: export PATH=$PATH:/home/cps/Documents/blockchain/23.istio/istio-1.20.3/bin

# Intall istio using the default profile

istioctl install --set profile=default -y

# For Installtion of multicluster istio service mesh

https://istio.io/latest/docs/setup/install/multicluster/primary-remote_multi-network/

# Label the namespace for automatic sidecar injection

kubectl get ns  --show-labels

kubectl label namespace default istio-injection=enabled

kubectl label namespace demo istio-injection=enabled

kubectl get namespace -L istio-injection

istioctl install --set profile=default --set values.proxy.holdApplicationUntilProxyStarts=true

istioctl install --set values.global.proxy.holdApplicationUntilProxyStarts=true

# Delete All

istioctl uninstall --purge

# Apply kubectl to create promotheus and grafana

kubectl apply -f addons

# For External ip installed metalLb 

Go to Metallb folder 

Kubectl apply -f 01_metallb.yaml

OR

kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.3/config/manifests/metallb-native.yaml

As per your requirement of ip address pool then apply 

kubectl apply -f 02_metallb-config.yaml

Install nginx application with laod-balancer

kubectl apply -f 03_test-load-balancer.yaml




