# Rockit Standard Library

The standard library for the [Rockit](https://github.com/dark-matter-tech) programming language. 24 modules across 6 domains covering core utilities, encoding, file I/O, networking (HTTP/1.1 through HTTP/3), security, testing, and time.

## Usage

Import modules with dot-separated paths:

```kotlin
import rockit.encoding.json
import rockit.core.collections
import rockit.networking.http
import rockit.security.tls
import rockit.testing.probe
```

## Modules

### Core

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| Collections | `rockit.core.collections` | — | List map, filter, fold, sort, zip, flatten, distinct |
| Math | `rockit.core.math` | — | Integer/float math, trig, gcd, lcm, constants |
| Strings | `rockit.core.strings` | — | Pad, repeat, join, split, replace, truncate |
| Result | `rockit.core.result` | — | Result type (Success/Failure) for error handling |
| UUID | `rockit.core.uuid` | RFC 9562 | UUID v4 random generation |

### Encoding

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| Base64 | `rockit.encoding.base64` | RFC 4648 | Base64 encode/decode |
| HPACK | `rockit.encoding.hpack` | RFC 7541 | Header compression for HTTP/2 |
| JSON | `rockit.encoding.json` | RFC 8259 | JSON parse, stringify, pretty-print, auto-wrap |
| QPACK | `rockit.encoding.qpack` | RFC 9204 | Header compression for HTTP/3 |
| XML | `rockit.encoding.xml` | W3C XML 1.0 | XML parsing, generation, JSON bridge |

### Filesystem

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| File I/O | `rockit.filesystem.file` | — | Read, write, exists, delete files |
| Path | `rockit.filesystem.path` | — | Join, dir, base, ext, normalize paths |

### Networking

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| HTTP | `rockit.networking.http` | RFC 9110/9112 | HTTP/1.1 client (GET/POST/PUT/DELETE, HTTPS) |
| HTTP/2 | `rockit.networking.http2` | RFC 9113 | HTTP/2 multiplexed streams and frames |
| HTTP/3 | `rockit.networking.http3` | RFC 9114 | HTTP/3 over QUIC with QPACK compression |
| QUIC | `rockit.networking.quic` | RFC 9000 | QUIC transport with variable-length integers |
| URL | `rockit.networking.url` | RFC 3986 | URL parsing, percent-encoding, query parameters |
| WebSocket | `rockit.networking.websocket` | RFC 6455 | WebSocket client with frame encoding |

### Security

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| TLS | `rockit.security.tls` | RFC 8446/5246 | TLS 1.2/1.3 handshake and record protocol |
| Crypto | `rockit.security.crypto` | FIPS 180-4/197 | SHA, HMAC, AES cryptographic primitives |
| X.509 | `rockit.security.x509` | RFC 5280 | Certificate parsing and validation |
| PEM | `rockit.security.pem` | RFC 7468 | PEM encoding/decoding for certificates and keys |

### Testing & Time

| Module | Import | Standard | Description |
|--------|--------|----------|-------------|
| Probe | `rockit.testing.probe` | — | Test assertions for `@Test` annotated functions |
| DateTime | `rockit.time.datetime` | ISO 8601 | Date/time formatting, epoch conversion, leap years |

## RFC Test Vectors

The encoding and networking modules include byte-exact conformance tests against official RFC test vectors. See the [RFC Test Vectors](../../wiki/RFC-Test-Vectors) wiki page for details.

| RFC | Appendix | Module | Tests |
|-----|----------|--------|-------|
| RFC 7541 | C.1–C.5 | HPACK | Integer encoding, field representations, request/response sequences |
| RFC 9000 | A.1 | QUIC | Variable-length integer encoding (1/2/4-byte, non-minimal) |
| RFC 9204 | B.1–B.4 | QPACK | Literal fields, dynamic table inserts, post-base references, duplicate |

## Installation

The standard library ships with Rockit. When building the compiler from source, launchpad is included as a git submodule at `RockitCompiler/Stage1/stdlib`.

```bash
git clone --recurse-submodules https://github.com/dark-matter-tech/moon.git
```

## Running Tests

```bash
# Run all tests
rockit test --scheme all

# Run by domain
rockit test --scheme encoding
rockit test --scheme networking
rockit test --scheme security

# Run a single test file
rockit test tests/encoding/test_hpack.rok
```

## Structure

```
rockit/
├── core/
│   ├── collections.rok    # List map/filter/fold/sort/zip/flatten
│   ├── math.rok           # Integer & float math, trig, constants
│   ├── strings.rok        # Pad, repeat, join, split, replace
│   ├── result.rok         # Result type (Success/Failure)
│   └── uuid.rok           # UUID v4 generation
├── encoding/
│   ├── base64.rok         # Base64 encode/decode (RFC 4648)
│   ├── hpack.rok          # HPACK header compression (RFC 7541)
│   ├── json.rok           # JSON encoder/decoder (RFC 8259)
│   ├── qpack.rok          # QPACK header compression (RFC 9204)
│   └── xml.rok            # XML parser/generator (W3C XML 1.0)
├── filesystem/
│   ├── file.rok           # File I/O wrappers
│   └── path.rok           # Path join/dir/base/ext/normalize
├── networking/
│   ├── http.rok           # HTTP/1.1 client (RFC 9110)
│   ├── http2.rok          # HTTP/2 frames and streams (RFC 9113)
│   ├── http3.rok          # HTTP/3 over QUIC (RFC 9114)
│   ├── quic.rok           # QUIC transport (RFC 9000)
│   ├── url.rok            # URL parser and encoder (RFC 3986)
│   └── websocket.rok      # WebSocket client (RFC 6455)
├── security/
│   ├── crypto.rok         # SHA, HMAC, AES (FIPS 180-4/197)
│   ├── pem.rok            # PEM encoding (RFC 7468)
│   ├── tls.rok            # TLS 1.2/1.3 (RFC 8446)
│   └── x509.rok           # X.509 certificates (RFC 5280)
├── testing/
│   └── probe.rok          # Probe test framework (20+ assertions)
└── time/
    └── datetime.rok       # Date/time utilities (ISO 8601)
tests/
├── core/                  # Tests for core modules
├── encoding/              # Tests for encoding modules (incl. RFC vectors)
├── filesystem/            # Tests for filesystem modules
├── networking/            # Tests for networking modules (incl. RFC vectors)
├── security/              # Tests for security modules
├── testing/               # Tests for testing module
└── time/                  # Tests for time module
```

## Contributing

Contributions are welcome. Please open an issue or pull request on [GitHub](https://github.com/dark-matter-tech/launchpad).

## License

Apache 2.0. Copyright 2026 Dark Matter Tech.
