# Cybersecurity and National Defence Ex. 8
## A.Y. 2025/2026

### Contacts
* **Flavio Ciravegna:** [*flavio.ciravegna@polito.it*]
* **Silvia Sisinni:** [*silvia.sisinni@polito.it*]
* **Enrico Bravi:** [*enrico.bravi@polito.it*]
* **Lorenzo Ferro:** [*lorenzo.ferro@polito.it*]

---

## Overview

This document contains examples of questions for the Cybersecurity and National Defence exam. These examples are intended to give students an idea of the type of questions that may appear in the exam, but they are **not exhaustive** and should **not** be used as a substitute for studying the course material.

### Exam Information
- **Duration:** 90 Minutes.
- **21 or 22 total questions**
    - **17 multiple choice questions:** on cybersecurity-related topics
        - 1 to many possible answers can be correct
            - 1 correct answer -> answer worth 100%;
            - 2 correct answers -> each answer worth 50%;
            - and so on...
        - Penalties apply to wrong answers
            - each wrong answer is worth -25% of the full score;
            - **note: you can reach a negative score**.
    - **1 or 2 open questions:** on cybersecurity-related topics;
        - 1 complex question;
        - or 2 simpler questions (but overall scoring remains the same).
        - **no penalties applied to wrong answers**.
    - **3 multiple choice questions** on the first lectures (common to all *Grandi Sfide* courses).
- Devices:
    - **No laptop is needed**
        - the exam will be on paper.
    - **Mobile phones not allowed**.
    - Calculators can be used, if needed.


- **Maximum Exam Score: 33 points**
    - **Written Exam**: up to 21 points
        - passed with score >= **12 points**
    - **Projects**: up to 12 points
        - Group Project **NOT mandatory** to pass the exam.
    - Exam passed with score >= **18 points**
    - 30L if score >= **31 points**

### Exam Grade Recording Policy
- **Written exam ≥ 18** AND **NOT assigned** to any group
    - grade automatically recorded.
- **Written exam ≥ 18** AND **assigned** to a project group
    - grade recorded only **after** the group project is completed.
- **Written exam ≥ 12** AND **Project completed** BUT **you want to improve your grade**
    - send an email with the request to **NOT** record the grade.
    - you may retake the **written exam** in the next exam call.

---

## Part 1: Open Questions
*Please answer the following questions clearly and concisely. You have approximately 15-20 minutes for this section.*

**Question 1 (example of simple question)**

Two IoT devices, Device A and Device B, communicate over an insecure wireless network.
A shared symmetric key has been installed on both devices during manufacturing. The devices must ensure the integrity and authenticity of their messages and detect any tampering or impersonation. Propose a secure communication mechanism between the two devices using
appropriate cryptographic primitives. Constraints: (5)
- Devices have limited computational resources.
- Messages are short and frequent.
- Assume an attacker can intercept and replay messages.

***Answer:***
Choose between a MAC or digital signature for ensuring message integrity and authentication.

Cryptographic Tools Chosen: Message Authentication Code (MAC)
Why MAC and not Digital Signature? MACs are efficient and ideal for constrained devices. Digital signatures are computationally expensive and unnecessary if a shared key already exists.

Protocol:
1. Device A → Device B
    - Message, Timestamp, MAC_K(Message || Timestamp)
2. Device B verifies:
    - The timestamp is recent (to prevent replay attacks).
    - The MAC is valid using the shared secret key K.

*Justification:* MAC ensures message integrity and authentication. Timestamp mitigates replay attacks.
The symmetric nature of MAC is more efficient than digital signatures for frequent, short
messages.

**Question 2 (another example of simple question)**

Describe how CTR mode works. Include a brief explanation and a diagram or pseudocode. Identify and
explain a major vulnerability or limitation of CTR mode. (4)

***Answer:***
CTR (Counter) mode is a block cipher mode of operation that turns a block cipher into a stream cipher.
Instead of directly encrypting the plaintext blocks, CTR mode encrypts a counter value and then XORs the result with the plaintext to produce the ciphertext.

- A nonce (number used once) and a counter are combined to form a unique input block for each encryption operation.
- This input is encrypted using the block cipher (e.g., AES), and the output is XORed with the plaintext to get the ciphertext.
- For decryption, the same counter values are encrypted and XORed with the ciphertext to recover the plaintext.
Vulnerability or Limitation of CTR Mode

A major vulnerability of CTR mode is that reusing the *same nonce* with the *same key* leads to keystream reuse, which can result in a serious compromise of confidentiality.

**Question 3 (example of complex question)**

Which cryptographic primitives, and how, should be adopted to guarantee the 3 cybersecurity pillars (CIA Triad) and authentication?

Immagine a situation where two parties need to exchange data while guaranteeing the respective CIA properties and message authentication. Discuss, for each of the pillars (Confidentiality, Integrity, Availability) and authentication, what cryptographic primitives and tools you should use; you should support your answer with a diagram depicting the
step by step protocols adopted.

Constraints:
- No previous keys are shared between the two party.
- The two parties are using resource constrained devices to exchange data (e.g., some IoT device).

***Answer:***
*This list contains the concepts that needs to be mentioned in the answer, not the full answer itself. Obviously, it must be expressed in a clear way.*

- Key exchange: Diffie-Hellman (3)
- Symmetric Encryption -> After exchanging keys with DH, encrypt data with symmetric encryption.
For instance, I can use AES to encrypt the data (**confidentiality**). This is better than using asymmetric encryption since it is more computationally efficient. (3)
- I can use MAC to guarantee **authentication** and **integrity**. (4)
- In theory, it would be possible to use Asymmetric Encryption instead of symmetric encryption to encrypt data, but it is more computationally expensive. However, it can be used to exchange keys, as done with Diffie-Hellman.

---

## Part 2: Multiple-Choice Questions (Cybersecurity)

**1. Which of the following statements correctly describe the characteristics of IT (Information Technology) and OT (Operational Technology) systems?**
- **A.** IT systems primarily manage computation, business applications, and data.
- **B.** OT systems primarily monitor and control physical devices, processes, and events.
- **C.** OT systems were traditionally built to be always connected to the Internet.
- **D.** IT systems typically prioritize availability over data confidentiality.

**Correct Answer(s):** A, B

**2. What is the *"CIA triad"*?**
- **A.** Confidentiality, Integrity, Authentication
- **B.** Confidentiality, Integrity, Availability
- **C.** Confidentiality, Isolation, Availability
- **D.** Cardinality, Integrity, Authentication

**Correct Answer:** B

**3. In the context of risk management, which of the following correctly defines the relationship between an asset and risk?**
- **A.** Risk is a static value, independent of the value or criticality of an asset.
- **B.** Impact analysis evaluates an asset's criticality to determine the severity of a potential loss, which is a core component of evaluating risk.
- **C.** An asset refers to the probability of a harmful cyber event occurring.
- **D.** Only tangible physical assets can be subjected to cyber risks.

**Correct Answer:** B

**4. What does the property of "Non-repudiation" guarantee in information security?**
- **A.** The ability to verify the biological identity of the user requesting access.
- **B.** The protection against an entity falsely denying having performed a particular action (e.g., sending a message).
- **C.** The timely and reliable access to and use of information systems.
- **D.** The prevention of unauthorized disclosure of data to third parties.

**Correct Answer:** B

**5. In the context of cryptographic countermeasures, a Message Authentication Code (MAC) is used to guarantee which of the following security properties?**
- **A.** Integrity of the message.
- **B.** Authenticity of the message's origin.
- **C.** Confidentiality of the data during transmission.
- **D.** Non-repudiation, since it uses asymmetric cryptography.

**Correct Answer(s):** A, B

**6. In Access Control Models, what does "RBAC" stand for and what is its decision basis?**
- **A.** Rule-Based Access Control; decisions are based on environmental attributes and constraints.
- **B.** Role-Based Access Control; decisions are based on assigned organizational roles.
- **C.** Risk-Based Access Control; decisions are based on the probability of an ongoing attack.
- **D.** Resource-Based Access Control; decisions are based on the ownership of the object.

**Correct Answer:** B

**7. Which of the following statements correctly distinguishes "Privacy" from "Secrecy"?**
- **A.** Privacy is concerned with corporate intellectual property, while secrecy is about individual rights.
- **B.** Secrecy protects the individual's personal sphere, while privacy protects state or institutional information.
- **C.** Privacy protects the individual's personal sphere and autonomy, whereas secrecy protects sensitive institutional or state information to prevent harm from disclosure.
- **D.** Privacy and secrecy are identical concepts under the European GDPR framework.

**Correct Answer:** C

**8. Which data protection mechanism specifically replaces direct identifiers with reversible tokens to reduce risk?**
- **A.** Anonymization
- **B.** Pseudonymization
- **C.** Degaussing
- **D.** Logging

**Correct Answer:** B

**9. What is the main difference between a Weakness (e.g., listed in the CWE) and a Vulnerability (e.g., listed in the CVE)?**
- **A.** A weakness is a specific flaw in a specific software version, while a vulnerability is a general design error.
- **B.** A weakness is a class of security bug, while a vulnerability is a specific exploitable instance of a bug in a real system.
- **C.** Weaknesses are exclusively found in hardware, whereas vulnerabilities are only found in software.
- **D.** A vulnerability requires physical access to exploit, whereas a weakness can always be exploited remotely.

**Correct Answer:** B

**10. What does the Linux Integrity Measurement Architecture (IMA) measure?**
- **A.** Executables, shared libraries, and kernel modules.
- **B.** Application memory at runtime.
- **C.** Configuration files.
- **D.** Network traffic.

**Correct Answer:** A, C

**11. What is a Root of Trust?**
- **A.** A component that must always behave as expected since its misbehavior cannot be detected.
- **B.** The only component that is based on trusted functionalities.
- **C.** A component that enforces the system's security policies.
- **D.** A component that is always trusted and cannot be compromised by any attack.

**Correct Answer:** A

**12. In the context of Remote Attestation, what is an Evidence?**
- **A.** A claim, produced by the Attester, about its identity and integrity state.
- **A.** A claim, produced by the Endorser, about its identity and integrity state.
- **C.** A claim, produced by the Relying Party, about its identity and integrity state.
- **D.** A claim, produced by the Attester, that the Verifier can use to make an access/trust decision.

**Correct Answer:** A

**13. In a standard Operating System architecture, user applications typically execute in ____, whereas the core OS functions and hardware interactions execute in  ____.**
- **A.** user mode; kernel mode
- **B.** user mode; operating system mode
- **C.** kernel mode; user mode
- **D.** trusted mode; untrusted mode

**Correct Answer:** A

**14. Which cognitive bias is characterized by unskilled individuals overestimating their own competence, making them more vulnerable to manipulation because they lack the capacity to recognize their own errors?**
- **A.** Confirmation bias
- **B.** The Dunning-Kruger effect
- **C.** Availability heuristic
- **D.** Authority bias

**Correct Answer:** B

**15. A highly targeted phishing attack aimed specifically at C-level executives (such as CEOs or CFOs) to authorize large payments or wire transfers is known as:**
- **A.** Vishing
- **B.** Smishing
- **C.** Whaling
- **D.** Baiting

**Correct Answer:** C

**16. An attacker leaves a malware-infected USB drive in a company parking lot, hoping an employee will pick it up and plug it into their workstation out of curiosity. What is the name of this social engineering technique?**
- **A.** Dumpster Diving
- **B.** Tailgating
- **C.** Baiting
- **D.** Piggybacking

**Correct Answer:** C

**17. Which of the following are physical or hardware-based methods used to securely destroy or sanitize magnetic hard disks?**
- **A.** Shredding
- **B.** Degaussing
- **C.** Formatting the drive
- **D.** Using data wiping software

**Correct Answer(s):** A, B

**18. In a cybersecurity architecture, the "Weakest Link" principle implies that:**
- **A.** The overall security of any system is only as strong as its most vulnerable component.
- **B.** Attackers usually attempt to target the strongest component first.
- **C.** Attackers usually attempt to target the weakest component first.
- **D.** For each weak component, the system design must provide a strong countermeasure.

**Correct Answer:** A

**19. In symmetric cryptography, what is the primary purpose of Authenticated Encryption (AE), such as Galois/Counter Mode (GCM)?**
- **A.** To encrypt data using asymmetric public-private key pairs exclusively.
- **B.** To provide both confidentiality and integrity at the same time.
- **C.** To generate digital certificates.
- **D.** To exchange session keys securely over an untrusted public channel.

**Correct Answer:** B

**20. Which of the following are characteristics of asymmetric cryptography?**
- **A.** It uses the same secret key for both encryption and decryption operations.
- **B.** It relies on cryptographic key pairs where one is kept private and the other is distributed publicly.
- **C.** It is typically much faster than symmetric cryptography and is used for encrypting large amounts of data.
- **D.** It is typically much slower than symmetric cryptography and is used for encrypting small amounts of data, such as keys.
**Correct Answer(s):** B, D

**21. What is the primary purpose of a "System Call" in an Operating System?**
- **A.** To provide an interface for user applications to request services from the kernel.
- **B.** To manage the physical components of the CPU directly from user space.
- **C.** To act as a bootloader that loads the OS into main memory during device startup.
- **D.** To evaluate network packets and define the firewall security policy of the system.
**Correct Answer:** A

**22. In the Remote Attestation protocol, what is the purpose of a *nonce* provided by the Verifier?**
- **A.** To encrypt the measurements before sending them back to the Verifier over an insecure network.
- **B.** To guarantee freshness and prevent replay attacks where an attacker reuses old evidences.
- **C.** To securely authenticate the Privacy CA that issued the Attestation Key.
- **D.** To sign the measurements before sending them to the Verifier over an insecure network.
**Correct Answer:** B

---