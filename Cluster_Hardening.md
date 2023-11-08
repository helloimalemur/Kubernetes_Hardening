#### [Back](README.md)
## Cluster Hardening

#### [Update Kubernetes frequently](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-upgrade/)
#### [Pod Security Policies /Pod Security Admission](https://kubernetes.io/docs/concepts/security/pod-security-admission/)
#### [Control anonymous requests to Kube-apiserver](https://kubernetes.io/docs/reference/access-authn-authz/authentication/#anonymous-requests)
#### [Enable Access authentication and authorization](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)
    ~~In Kubernetes 1.6+ anonymous requests are enabled by default.~~
    
    Kubernetes assumes that a cluster-independent service manages user authentication.
    Anonymous requests are not rejected in a default setup, a request without a token
    present would be performed as an anonymous request.

    Anonymous requests should be disabled by
    passing the ```--anonymous-auth=false``` option to the API server. Leaving anonymous
    requests enabled could allow a cyber actor to access cluster resources without
    authentication.

#### [Controlling Access to the Kubernetes API](https://kubernetes.io/docs/concepts/security/controlling-access/#api-server-ports-and-ips)

### **Example Network Policy**:
#### Deny all egress and Deny all ingress, with one ingress port opened for NodePort 37080 for service with label selector "drone: server"
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

#### [Use Role-Based Access Controls to minimize exposure]()
    Handy site collects together articles, tools and the official documentation all in one place
    Simplify Kubernetes Resource Access Control using RBAC Impersonation

### Disable and avoid insecure defaults
#### [disable default service accounts](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#use-the-default-service-account-to-access-the-api-server) & minimize permissions on newly created ones
    Exercise caution in using service accounts e.g.
    Opt out of automounting API credentials for a service account

### Ensure immutability of containers at runtime
#### [Principles of Container-based Application Design](https://kubernetes.io/docs/tasks/debug-application-cluster/audit/)


Setup appropriate OS-level security domains e.g. using PSA, OPA, security contexts
#### [Pod Security Admission](https://kubernetes.io/docs/tasks/configure-pod-container/migrate-from-psp/)

    define different isolation levels for Pods.

#### [Open Policy Agent](https://kubernetes.io/blog/2019/08/06/opa-gatekeeper-policy-and-governance-for-kubernetes/)

    can be leveraged to help enforce policies and strengthen governance in your Kubernetes environment.

#### [Manage kubernetes secrets](https://kubernetes.io/docs/concepts/configuration/secret/)

#### [Implement pod to pod encryption by use of mTLS](https://kubernetes.io/docs/tasks/tls/managing-tls-in-a-cluster/)
    Use container runtime sandboxes in multi-tenant environments (e.g. gvisor, kata containers)
    Implement pod to pod encryption by use of mTLS
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