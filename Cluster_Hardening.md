## Cluster Hardening

#### [Update Kubernetes frequently](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-upgrade/)

#### [Restrict access to Kubernetes API](https://kubernetes.io/docs/reference/access-authn-authz/controlling-access/)
#### [Control anonymous requests to Kube-apiserver](https://kubernetes.io/docs/reference/access-authn-authz/authentication/#anonymous-requests)
    ~~In Kubernetes 1.6+ anonymous requests are enabled by default.~~
    
    Kubernetes assumes that a cluster-independent service manages user authentication.
    Anonymous requests are not rejected in a default setup, a request without a token
    present would be performed as an anonymous request.

    Anonymous requests should be disabled by
    passing the ```--anonymous-auth=false``` option to the API server. Leaving anonymous
    requests enabled could allow a cyber actor to access cluster resources without
    authentication.

#### [Controlling Access to the Kubernetes API](https://kubernetes.io/docs/concepts/security/controlling-access/#api-server-ports-and-ips)

### **Example**:
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
#### [disable defaults](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#use-the-default-service-account-to-access-the-api-server) & minimize permissions on newly created ones
    Exercise caution in using service accounts e.g.
    Opt out of automounting API credentials for a service account

### Ensure immutability of containers at runtime
[Principles of Container-based Application Design](https://kubernetes.io/docs/tasks/debug-application-cluster/audit/)