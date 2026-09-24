# 🛡️ Threat Model & 4C Security Framework

The FinServ Digital Kubernetes platform design follows the **Cloud-Native 4C Security Model**, which nests controls from the outside in to ensure multiple layers of defense.

## 1. Cloud Layer ☁️
Protects the underlying infrastructure[cite: 3].
*   **Provider-level WAF:** Filters malicious traffic before it hits the cluster[cite: 3].
*   **Key Management Service (KMS):** Protects the encryption keys at the hardware level[cite: 3].
*   **IAM:** Secures access to the cloud provider accounts[cite: 3].

## 2. Cluster Layer ☸️
Secures the Kubernetes control plane and network[cite: 3].
*   **Namespace Isolation:** Partitions workloads into four domains (`platform`, `customer`, `payments`, `risk`) to contain blast radiuses[cite: 3].
*   **Network Policy:** Enforces a default-deny eBPF micro-segmentation where services cannot talk unless explicitly allowed[cite: 3].
*   **RBAC:** Maps least-privilege roles directly to an enterprise OIDC identity provider[cite: 3].

## 3. Container Layer 📦
Secures the execution environment of the applications[cite: 3].
*   **Image Provenance:** Cryptographically signs images using Cosign and verifies them at admission[cite: 3].
*   **Pod Security Standards:** Forces containers to run as non-root, with read-only root filesystems, and drops all Linux kernel capabilities[cite: 3].

## 4. Code Layer 💻
Secures the application data and logic[cite: 3].
*   **Dependency Scanning:** Blocks builds automatically on CRITICAL or HIGH CVEs via Trivy[cite: 3].
*   **Secure Secrets Handling:** Uses HashiCorp Vault Agent sidecars to inject short-lived, dynamically leased credentials directly into memory, avoiding plaintext static secrets[cite: 3].
