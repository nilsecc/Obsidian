
# Key Exchange

Allow two parties to exchange cryptographic keys securely.

**Diffie-Hellman**

- Agree on a key without previous messages
- Used in `TLS` (encryption for HTTP messages)

![[Pasted image 20260128123426.png]]

**RSA**

- Based on large prime numbers `p` and `q`
- Security relies on the difficulty of factoring n (n = p*q)
- Used in encryption and `signing`
- Also in `SSL` and `TLS`
- PKINIT used by kerberos
	- Uses public key cryptography (certificates)
	- The user authenticates using a private key
	- No password-derived key is sent
	- The user proves possession of the private key via a challenge–response
- Protecting sensible data

![[Pasted image 20260128125016.png]]

**ECDSA**

Elliptic Curve Digital Signature Algorithm uses ECC (Elliptic Curve Criptography) 
- Used for example in Bitcoin for generating pubKeys
![[Pasted image 20260128125300.png]]
---

![[Pasted image 20260128125753.png]]

# IKE (Internet Key Exchange)

Protocol IKE is used to securely negotiate cryptographic keys and authenticate peers for IPsec, which operates at the IP layer and can encrypt all traffic, such as in VPNs. Application-layer protocols like HTTPS may still use TLS on top of IPsec.
- Used In VPN
- Uses DH and cryptographic functions to exchange keys and parameters for encripting traffic
- DH can use RSA for key exchange and digital signatures and AES for ecripting data

**main mode**
- Default mode of IKE and more secure. 
- 3 phases each one exchanging different parameters
- slower

**Agressive mode**
- 2 phases, all parameters sent in the first
- faster

**PSK (Pre-Shared Keys)**
- Secret value shared between two parties 
- It authentificates the client to start an IKE with the VPN service for example
- Difficult to find a way to share this key before the IKE

```
CLIENTE                               SERVIDOR VPN
   |                                       |
   |---- (1) IKE_SA_INIT ----------------->|
   |      - algoritmos                     |
   |      - nonce                          |
   |      - Diffie-Hellman (valor público) |
   |                                       |
   |<--- (2) IKE_SA_INIT ------------------|
   |      - algoritmos elegidos            |
   |      - nonce                          |
   |      - Diffie-Hellman (valor público) |
   |                                       |
   |==== Ambos calculan CLAVE SECRETA =====|
   |==== (gracias a Diffie-Hellman) =======|
   |                                       |
   |---- (3) IKE_AUTH -------------------->|
   |      - ID del cliente                 |
   |      - AUTH (calculado usando PSK)    |
   |      - protegido con la clave DH      |
   |                                       |
   |<--- (4) IKE_AUTH ---------------------|
   |      - ID del servidor                |
   |      - AUTH (calculado usando PSK)    |
   |      - protegido con la clave DH      |
   |                                       |
   |==== IKE SA ESTABLECIDA (CANAL SEGURO) |
   |                                       |
   |---- (5) CREATE_CHILD_SA ------------->|
   |      - parámetros IPsec               |
   |                                       |
   |<--- (6) CREATE_CHILD_SA --------------|
   |                                       |
   |==== IPsec SA (ESP ACTIVO) ============|
   |                                       |
   |---- (7) DATOS CIFRADOS (ESP) -------->|
   |<--- (7) DATOS CIFRADOS (ESP) ---------|

```


# Authentification Protocols

Used for verifying the identity of users
![[Pasted image 20260128133224.png]]

# TCP/UDP Connections

**TCP**
- Connection protocol to transmit important data that can not be lost like web

**UDP**
- Connectionless protocol to transmit data thatn can be lost (FAST) like games or video streaming

**IP packet**

Packets made in the network layer, to transmir data from one computer to an other
- header + payload

IP header: 
![[Pasted image 20260128162953.png]]
![[Pasted image 20260128163259.png]]
We can see from the output that two different IP addresses are sending packets to IP address 10.129.1.1. However, from the IP ID, we can see that the packets are continuous. This strongly indicates that the two IP addresses belong to the same host in the network

IP Record-Route Field:
- Used to see the trace that the packet took to arrive
![[Pasted image 20260128163603.png]]

Also we can use `traceroute` more precissely
- it adds in 1 every time the TTL to see how many hops and the ip 

![[Pasted image 20260128163941.png]]

`Blind Spoofing`:
![[Pasted image 20260128164051.png]]

# Criptography

Encryption protects data confidentiality and integrity. Data is transformed using algorithms so unauthorized users cannot read it. Uses symmetric or asymmetric keys. Modern algorithms with long keys are highly secure.

**Symmetric Encryption**  
Uses the same key for encryption and decryption. Key must be shared securely. Efficient for large data. Examples: AES (most secure today), DES. Key management is critical.

**Asymmetric Encryption**  
Uses a public key for encryption and a private key for decryption. Solves key exchange problem. Enables digital signatures and authentication. Examples: RSA, PGP, ECC. Used in SSL/TLS, VPNs, SSH, PKI, e-signatures, cloud.

**DES (Data Encryption Standard)**  
Symmetric block cipher, 64-bit blocks, 56-bit effective key. Encrypts each block individually. Vulnerable to attacks due to short key. 3DES applies triple encryption (encrypt-decrypt-encrypt) for more security.

**AES (Advanced Encryption Standard)**  
Successor of DES. Supports 128, 192, 256-bit keys. Faster than DES, can encrypt multiple blocks simultaneously. Widely used in IPsec, SSH, VoIP, WLAN, PGP, OpenSSL.

**Cipher Modes**  
Define how block ciphers process data.

- **ECB:** simple, insecure, reveals patterns.
    
- **CBC:** common, used in AES, TLS, SSL, TrueCrypt.
    
- **CFB:** good for real-time streams, used in PKCS, BitLocker.
    
- **OFB:** good for data streams, key stream generated efficiently, used in PKCS, SSH.
    
- **CTR:** encrypts streams, used in IPsec, BitLocker.
    
- **GCM:** provides confidentiality + integrity, used in VPNs, wireless protocols.