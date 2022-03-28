You have to specify driver you want to use with minikube, in this case it will be hyperv. So in order to start minikube you have to run

**minikube start --vm-driver=hyperv**

If Hyperv was not previously enabled you have to run Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All and reboot your machine.

If you want to use hyper-v as default driver you can run minikube config set driver hyperv

