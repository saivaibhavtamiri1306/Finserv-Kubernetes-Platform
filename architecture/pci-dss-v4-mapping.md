# 📋 PCI-DSS v4.0 Compliance Mapping Matrix

This matrix serves as the primary artefact presented to the Qualified Security Assessor (QSA) during the RBI-regulated PCI-DSS Level 1 audit[cite: 3]. Each row traces a regulatory requirement through to the specific technical control that satisfies it and the evidence artefact that proves it[cite: 3].

| Requirement | Regulatory Intent | Technical Control | Evidence Artefact |
| :--- | :--- | :--- | :--- |
| **Req. 1** | Install and maintain network security controls[cite: 3] | Default-deny NetworkPolicies; domain namespace isolation; eBPF east-west microsegmentation[cite: 3] | NetworkPolicy manifests; Calico verification logs[cite: 3] |
| **Req. 2** | Apply secure configurations to all system components[cite: 3] | Restricted Pod Security Standard; rootless execution; immutable filesystems; CIS benchmark hardening[cite: 3] | Kyverno audit reports; kube-bench logs[cite: 3] |
| **Req. 3** | Protect stored account data[cite: 3] | Vault Transit field-level PAN encryption; etcd envelope encryption at rest (KMS)[cite: 3] | Vault transit audit logs; KMS validation[cite: 3] |
| **Req. 4** | Protect cardholder data in transit[cite: 3] | Linkerd mTLS mesh; TLS 1.3 edge termination[cite: 3] | Linkerd mTLS metrics; SSL Labs A+ verification[cite: 3] |
| **Req. 6** | Develop and maintain secure systems and software[cite: 3] | Distroless images; Trivy scanning; Cosign signing and admission control[cite: 3] | CI/CD build traces; Sigstore signature logs[cite: 3] |
| **Req. 7** | Restrict access by business need to know[cite: 3] | Least-privilege RBAC; persona separation; OIDC-backed SSO[cite: 3] | RoleBinding definitions; IAM audit logs[cite: 3] |
| **Req. 8** | Identify and authenticate access to components[cite: 3] | No default token automounting; ephemeral developer tokens; Vault identity engine[cite: 3] | API server auth configs; Vault lease records[cite: 3] |
| **Req. 10** | Log and monitor all access to system components[cite: 3] | Centralised 1-year immutable logging; API audit logging; Falco runtime detection[cite: 3] | Loki/OpenSearch retention policy; Falco dashboards[cite: 3] |
| **Req. 11** | Regularly test security of systems and networks[cite: 3] | Automated vulnerability scanning; runtime anomaly detection; isolated staging pen-tests[cite: 3] | Trivy daily scan reports; Falco event history[cite: 3] |
