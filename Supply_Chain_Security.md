#### [Back](README.md)
## Supply Chain Security


#### Minimize base image footprint
Use distroless, UBI minimal, Alpine, or relavent to your app nodejs, python but the minimal build.

#### Do not include uncessary software not required for container during runtime e.g build tools and utilities, troubleshooting and debug binaries.

#### [Learnk8s: 3 simple tricks for smaller Docker images](https://learnk8s.io/blog/smaller-docker-images)
#### [GKE 7 best practices for building containers](https://cloud.google.com/blog/products/gcp/7-best-practices-for-building-containers)
#### [Whitelist allowed image registries, sign and validate images](https://kubernetes.io/blog/2019/03/21/a-guide-to-kubernetes-admission-controllers/#why-do-i-need-admission-controllers)
#### [Using ImagePolicyWebhook admission Controller](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/#imagepolicywebhook)
#### [Static analysis of workloads (e.g. kubernetes resources, docker files)](https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/#7-statically-analyse-yaml)
#### [Scan images for known vulnerabilities](https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/#10-scan-images-and-run-ids)
#### [Scanning with Aqua security - Trivy](https://github.com/aquasecurity/trivy)
#### [Scanning on comand line via Anchore](https://github.com/anchore/anchore-cli#command-line-examples)
