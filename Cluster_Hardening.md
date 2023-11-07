## Cluster Hardening

1.
[Restrict access to Kubernetes API](https://kubernetes.io/docs/reference/access-authn-authz/controlling-access/)
[Control anonymous requests to Kube-apiserver](https://kubernetes.io/docs/reference/access-authn-authz/authentication/#anonymous-requests)
[Non secure access to the kube-apiserver](https://kubernetes.io/docs/concepts/security/controlling-access/#api-server-ports-and-ips)

2.
[Use Role-Based Access Controls to minimize exposure]()
Handy site collects together articles, tools and the official documentation all in one place
Simplify Kubernetes Resource Access Control using RBAC Impersonation

3.
Exercise caution in using service accounts e.g.
[disable defaults](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#use-the-default-service-account-to-access-the-api-server), minimize permissions on newly created ones
Opt out of automounting API credentials for a service account

4.
[Update Kubernetes frequently](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm-upgrade/)
