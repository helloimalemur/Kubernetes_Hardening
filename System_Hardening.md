# System Hardening


### Minimize host OS footprint (reduce attack surface)
    Apply host updates
    Install minimal required OS fingerprint
    Identify and address open ports
    Remove unnecessary packages
    Protect access to data with permissions
#### Appropriately use kernel hardening tools such as AppArmor, seccomp, Falco;
#### [The Falco Project - Cloud Native Runtime Security - used by AWS, IBM, RH etc](https://falco.org/docs/)
#### [seccomp which stands for secure computing was originally intended as a means of safely running untrusted compute-bound programs](https://kubernetes.io/docs/tutorials/clusters/seccomp/)
#### [AppArmor can be configured for any application to reduce its potential host attack surface and provide greater in-depth defense.](https://kubernetes.io/docs/tutorials/clusters/apparmor/)
#### [Pod Security](https://kubernetes.io/docs/concepts/security/pod-security-admission/)
#### [Restirct allowed hostpaths](https://kubernetes.io/docs/concepts/policy/pod-security-policy/#volumes-and-file-systems)

### Minimize IAM roles
#### [Enable Access authentication and authorization](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)
    Minimize external access to the network.
    With the following all pods can talk to all pods in all name spaces but not to the outside of the cluster.
