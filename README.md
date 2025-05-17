# charon
JWT library

# 🛡️ jose – A Go Library for JOSE (JWS, JWE, JWK, JWT)

`jose` is a modular, idiomatic Go library for working with [JOSE](https://datatracker.ietf.org/wg/jose/documents/) standards including:

- **JWS** (JSON Web Signature)
- **JWE** (JSON Web Encryption)
- **JWK** (JSON Web Key)
- **JWT** (JSON Web Token)
- **JWA** (JSON Web Algorithms)

This library emphasizes clear modularity, strong typing, and separation of concerns while staying true to Go best practices.

---

## 🚀 Features

- ✅ Sign and verify JWS messages (compact or JSON serialization)
- ✅ Create and validate JWTs with custom claims
- ✅ Parse and serialize JWKs (RSA, EC, symmetric keys)
- 🔒 (WIP) Encrypt and decrypt payloads using JWE
- 🔧 Minimal external dependencies, designed for embedding or extension

---

## 🗂️ Project Structure
<pre lang="markdown">
```
jose/
├── jws/                # JSON Web Signature
│   ├── signer.go       # Signs payloads using supported algorithms
│   ├── verifier.go     # Verifies signatures
│   ├── jws.go          # Encodes/decodes JWS messages
│   └── header.go       # Manages protected/unprotected headers
│
├── jwe/                # JSON Web Encryption (optional, for later)
│   ├── encrypter.go    # Encrypts payloads
│   ├── decrypter.go    # Decrypts payloads
│   └── jwe.go          # Encodes/decodes JWE messages
│
├── jwk/                # JSON Web Key
│   ├── jwk.go          # Common key interface and representation
│   ├── parse.go        # Parses JWK JSON into key objects
│   └── keytypes/       # Specific key types
│       ├── rsa.go
│       ├── ec.go
│       └── oct.go
│
├── jwa/                # JSON Web Algorithms
│   ├── alg.go          # Algorithm constants and registry
│   ├── hash.go         # Hash function helpers
│   ├── hmac.go         # HMAC implementation (HS256, etc.)
│   ├── rsa.go          # RSA signing/verification
│   └── ecdsa.go        # ECDSA signing/verification
│
├── jwt/                # JSON Web Token
│   ├── token.go        # JWT structure and serialization
│   ├── claims.go       # Standard claims: exp, aud, iss, etc.
│   └── parser.go       # Validates and parses JWTs
│
├── internal/           # Internal-only helper packages
│   ├── b64url/         # Base64URL encoding/decoding (RFC 7515)
│   │   └── b64url.go
│   ├── jsonutil/       # JSON marshal/unmarshal helpers
│   │   └── jsonutil.go
│   └── joseerr/        # Common error definitions for the JOSE lib
│       └── errors.go
│
└── go.mod              # Go module file
```
</pre>



## 📦 Module Overview

### `jws/` – JSON Web Signature
Handles creation, signing, and verification of JWS tokens using compact and JSON serialization formats.

- `signer.go`: Signs payloads with supported algorithms.
- `verifier.go`: Verifies JWS signatures.
- `jws.go`: Encodes/decodes compact and full JWS messages.
- `header.go`: Manages protected/unprotected headers.

---

### `jwe/` – JSON Web Encryption *(optional/advanced)*
Encrypts and decrypts payloads using RSA, AES, and other algorithms.

- `encrypter.go`: Encrypts payloads into JWE format.
- `decrypter.go`: Decrypts JWE payloads.
- `jwe.go`: Manages JWE encoding/decoding logic.

---

### `jwk/` – JSON Web Key
Parses and handles cryptographic keys in JWK format.

- `jwk.go`: Defines the core key interface and utilities.
- `parse.go`: Parses JWK JSON to Go key types.
- `keytypes/`: Type-specific key handling.
    - `rsa.go`: RSA public/private key support.
    - `ec.go`: EC key handling.
    - `oct.go`: Symmetric key support.

---

### `jwa/` – JSON Web Algorithms
Defines and implements the supported JOSE algorithms.

- `alg.go`: Algorithm registry and constants (`HS256`, `RS256`, etc.).
- `hash.go`: Helpers for selecting hash functions.
- `hmac.go`: HMAC signing and verification.
- `rsa.go`: RSA signing and verification.
- `ecdsa.go`: ECDSA support.

---

### `jwt/` – JSON Web Token
High-level JWT functionality built on JWS and JWE, including claims and validation.

- `token.go`: JWT token structure and handling.
- `claims.go`: Standard JWT claims like `exp`, `iat`, `aud`, `sub`.
- `parser.go`: Parses and validates JWTs.

---

### `internal/` – Internal Helpers (Private API)
Helpers organized into small, purpose-specific packages.

- `b64url/`: Base64URL encoding/decoding (RFC 7515-compliant, no padding).
- `jsonutil/`: Typed JSON marshal/unmarshal wrappers and helpers.
- `joseerr/`: Shared error types and constants across packages.

---

### `go.mod`
Go module definition for dependency management and versioning.