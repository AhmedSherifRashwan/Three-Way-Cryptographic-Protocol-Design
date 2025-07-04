# 🔐 HRSCEP: Secure Contract Exchange Protocol (6051CEM Coursework)

> 📘 *Module*: Practical Cryptography (6051CEM)  
> 👨‍🎓 *Author*: Ahmed Rashwan (SID: 12842713)  
> 🧑‍🏫 *Supervisor*: Dr. Derrick Newton  
> 📅 *Date Submitted*: 28/03/2025

---

## 📌 Project Overview

This project presents a **custom cryptographic communication protocol** called **HRSCEP** (H&R Secure Contract Exchange Protocol) for securely exchanging legally binding contracts between three parties:

- 🧑‍💼 The Buyer  
- 🧑‍⚖️ H&R (intermediary solicitor)  
- 🧑‍💼 The Seller’s Solicitor  

The protocol ensures confidentiality, integrity, authentication, non-repudiation, and compliance with UK laws using strong cryptographic techniques.

---

## 🔐 Key Features of HRSCEP

| Principle           | Implementation                                                                 |
|---------------------|---------------------------------------------------------------------------------|
| Confidentiality     | TLS 1.3 + AES-256                                                               |
| Integrity           | SHA-3 (512-bit) Hashing + RSA-4096 Digital Signatures                          |
| Availability        | Redundant secure servers + RFC-3161 timestamping authority                      |
| Authentication      | PKI (Public Key Infrastructure) + Mutual TLS (mTLS)                            |
| Authorization       | Role-Based Access Control (RBAC)                                               |
| Accounting          | RFC-5848 Signed Syslog + SQL Ledger                                            |
| Non-Repudiation     | RSA-4096 Signatures + SQL Ledger with cryptographic verification               |

---

## 🔁 Protocol Flow Summary

1. **Buyer** signs the contract using RSA-4096 + SHA-3 and submits to **H&R**.
2. **H&R** verifies integrity, timestamps the document (RFC 3161), and logs actions securely.
3. **H&R** forwards the signed contract to the **Seller’s solicitor** via TLS 1.3.
4. The seller’s solicitor responds, and the process is verified and completed with full audit trails.

📊 A diagram illustrating this process is included in the full report.

---

## 🧪 Sample Python Implementation

This repo includes Python code to:

- 📄 Extract contract text from a PDF
- ✍️ Digitally sign the contract using RSA-4096 & SHA3-512
- ✅ Verify digital signatures
- 📜 Log and print out summaries for audit trails

```python
# Sample: Digital Signing with RSA-4096 + SHA3-512
signature = private_key.sign(
    contract.encode("utf-8"),
    padding.PSS(
        mgf=padding.MGF1(hashes.SHA3_512()),
        salt_length=padding.PSS.MAX_LENGTH
    ),
    hashes.SHA3_512()
)
```

---

## ⚠️ Known Limitations

- 🐢 **Latency**: RSA-4096 is secure but computationally intensive
- 🧩 **Implementation Risk**: Complex cryptographic stack requires precise configuration
- 🛑 **Single Point of Trust**: RFC 3161 TSA (Timestamping Authority) is a central dependency

---

## ⚖️ Legal & Regulatory Compliance

✅ Compliant with:

- **UK eIDAS Regulation**  
- **Electronic Communications Act 2000**  
- **Data Protection Act 2018 (DPA)**

---

## 📂 Files Included

- `HRSCEP_protocol.py`: Python implementation of the contract signing & verification process  
- `contract_6051CEM_Test.pdf`: Example PDF used for signing  
- `README.md`: This file  
- `HRSCEP_Report.pdf`: Full project report with diagrams and references

---

## 📌 Conclusion

The **HRSCEP protocol** is a robust and legally compliant method for secure digital contract exchange. It incorporates strong encryption, digital signatures, timestamping, and full auditing, making it a resilient system for high-assurance legal and financial communications.

---

## 📜 References

- RFC 3161, RFC 5848, SHA-3 by NIST  
- Cloudflare (2024) on mTLS  
- UK Government Legislation (eIDAS, ECA 2000, DPA 2018)  
- Project-specific references available in full report
