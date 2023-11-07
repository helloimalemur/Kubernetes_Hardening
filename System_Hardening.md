## System Hardening


1. 
Minimize host OS footprint (reduce attack surface)
[seccomp which stands for secure computing was originally intended as a means of safely running untrusted compute-bound programs](https://kubernetes.io/docs/tutorials/clusters/seccomp/)
[AppArmor can be configured for any application to reduce its potential host attack surface and provide greater in-depth defense.](https://kubernetes.io/docs/tutorials/clusters/apparmor/)
[Pod Security](https://kubernetes.io/docs/concepts/security/pod-security-admission/)
Apply host updates
Install minimal required OS fingerprint
Identify and address open ports
Remove unnecessary packages
Protect access to data with permissions
[Restirct allowed hostpaths](https://kubernetes.io/docs/concepts/policy/pod-security-policy/#volumes-and-file-systems)

2. 
Minimize IAM roles
[Enable Access authentication and authorization](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)

3. 
Minimize external access to the network.
With the following all pods can talk to all pods in all name spaces but not to the outside of the cluster.

Example; Deny all egress and Deny all ingress, with one ingress port opened for NodePort 37080 for service with label selector "drone: server"
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-external-egress
spec:
  podSelector: {}
  policyTypes:
  - Egress
  egress:
    to:
    - namespaceSelector: {}
---
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
   name: default-deny-ingress
spec:
   podSelector:
      matchLabels:
         drone: server
   policyTypes:
      - Ingress
   ingress:
      - ports:
           - protocol: TCP
             port: 30780
```