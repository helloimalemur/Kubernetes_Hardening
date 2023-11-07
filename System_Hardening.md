## System Hardening


1. 
Minimize host OS footprint (reduce attack surface)
[seccomp which stands for secure computing was originally intended as a means of safely running untrusted compute-bound programs](https://kubernetes.io/docs/tutorials/clusters/seccomp/)
[AppArmor can be configured for any application to reduce its potential host attack surface and provide greater in-depth defense.](https://kubernetes.io/docs/tutorials/clusters/apparmor/)
[Pod Security](https://kubernetes.io/docs/concepts/security/pod-security-admission/)

2. 
Minimize IAM roles
[Enable Access authentication and authorization](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)