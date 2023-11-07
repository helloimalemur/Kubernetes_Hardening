## Minimize Microservice Vulnerabilities

Setup appropriate OS-level security domains e.g. using PSA, OPA, security contexts
#### [Pod Security Admission](https://kubernetes.io/docs/tasks/configure-pod-container/migrate-from-psp/)

    define different isolation levels for Pods.

#### [Open Policy Agent](https://kubernetes.io/blog/2019/08/06/opa-gatekeeper-policy-and-governance-for-kubernetes/)

    can be leveraged to help enforce policies and strengthen governance in your Kubernetes environment.

## [Security Contexts](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
    
#### [A security context defines privilege and access control settings for a Pod or Container.](Configure a Security Context for a Pod or Container)
    Security context settings include, but are not limited to -- 
    
    Discretionary Access Control -- Permission to access an object, like a file, is based on user ID (UID) and group ID (GID).
    
    Security Enhanced Linux (SELinux) --  Objects are assigned security labels.
    
    Running as privileged or unprivileged.
    
    Linux Capabilities --  Give a process some privileges, but not all the privileges of the root user.
    
    AppArmor --  Use program profiles to restrict the capabilities of individual programs.
    
    Seccomp --  Filter a process's system calls.
    
    allowPrivilegeEscalation --  Controls whether a process can gain more privileges than its parent process. This bool directly controls whether the no_new_privs flag gets set on the container process. allowPrivilegeEscalation is always true when the container: is run as privileged, or has CAP_SYS_ADMIN
    
    readOnlyRootFilesystem --  Mounts the container's root filesystem as read-only.

#### [Manage kubernetes secrets]()

    Use container runtime sandboxes in multi-tenant environments (e.g. gvisor, kata containers)
    Implement pod to pod encryption by use of mTLS
