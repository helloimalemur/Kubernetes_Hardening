#### [Back](README.md)
# System Hardening

### Minimize host OS footprint (reduce attack surface)
    -- Apply host updates
    -- Install minimal required OS fingerprint
    -- Identify and address open ports
    -- Remove unnecessary packages
    -- Protect access to data with permissions
## Appropriately use kernel hardening tools such as AppArmor, seccomp, Falco - etc
#### [The Falco Project - Cloud Native Runtime Security - used by AWS, IBM, RH etc](https://falco.org/docs/)
#### [seccomp (secure computing) was originally intended as a means of safely running untrusted compute-bound programs](https://kubernetes.io/docs/tutorials/clusters/seccomp/)
#### [AppArmor can be configured for any application to reduce its potential host attack surface and provide greater in-depth defense.](https://kubernetes.io/docs/tutorials/clusters/apparmor/)
