# buildah-azdoagent

In progress 

Repo contains the docker file for the azure devops self hosted agent + buildah in ubuntu:20.04

Also contains manifests for running the same in a controlled kubernetes env 


Steps; 

1. since buildah requires fuse-overlay 
2. run the fuse-overlay.yaml 
    Daemonset to expose the fuse-overlay using the k8s device plugin 
3. SSH to the nodes to add the custom apparmor profile for running buildah 

```sh 
sudo apparmor_parser buildah-appaprmor 
```

Todos 
1. support  for statefulsets instead of Deployments
2. support for Pvs for storing the images when pulled by buildah 
3. auotmate the apparmour profile, since the app aprmour profile needs to be added each node using 'apparmor_parser' 
4. possibly use https://github.com/sysdiglabs/kube-apparmor-manager for the same
#references 
https://flavio.castelli.me/2020/09/16/build-multi-architecture-container-images-using-kubernetes/