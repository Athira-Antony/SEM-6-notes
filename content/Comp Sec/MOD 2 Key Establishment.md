
- Key transport: One party creates the secret value and securely transfers it to the
other(s).
• Key agreement: Both parties contribute to the generation of the secret value so that no
party can predict the outcome.
• Key authentication: One party is assured that no other party aside from a speciﬁcally
identiﬁed second party may gain access to a particular secret key.
• Key conﬁrmation: One party is assured that a second (possibly unidentiﬁed) party has
possession of a particular secret key.
• Explicit key authentication: Both key authentication and key conﬁrmation hold.

![[Pasted image 20260223101559.png]]

### Diffie Hellman Protocol
- DH **does NOT encrypt any message**
- DH **does NOT authenticate** who you're talking to
- DH just **establishes a shared secret** — then that secret is used as a symmetric key for actual encryption
- Security based on **DLP** (Discrete Logarithm Problem)

### RSA
- **Encrypts messages** using public key
- **Decrypts messages** using private key
- **Creates digital signatures** to prove identity
- RSA **directly encrypts/ decrypt data**
- RSA can also **verify identity** (digital signatures)
- Security based on **IFP** (Integer Factorization Problem)
- Much **slower** than DH for key exchange

![[Pasted image 20260223101952.png]]

![[Pasted image 20260223105422.png]]

[[MOD 3 Hash And Digital signature]]
