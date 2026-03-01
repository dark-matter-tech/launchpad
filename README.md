# Launchpad — Rockit Standard Library

The standard library for the [Rockit](https://github.com/dark-matter-tech) programming language. 15 modules covering core utilities, I/O, networking, encoding, testing, and more.

## Usage

Import modules with dot-separated paths:

```kotlin
import rockit.json
import rockit.core.collections
import rockit.net.http
import rockit.test.probe
```

## Modules

| Module | Import | Description |
|--------|--------|-------------|
| Collections | `rockit.core.collections` | List map, filter, fold, sort, zip, flatten, distinct |
| Math | `rockit.core.math` | Integer/float math, trig, gcd, lcm, constants |
| Strings | `rockit.core.strings` | Pad, repeat, join, split, replace, truncate |
| Result | `rockit.core.result` | Result type (Success/Failure) for error handling |
| UUID | `rockit.core.uuid` | UUID v4 random generation |
| File I/O | `rockit.io.file` | Read, write, exists, delete files |
| Path | `rockit.io.path` | Join, dir, base, ext, normalize paths |
| HTTP | `rockit.net.http` | HTTP/1.1 client (GET/POST/PUT/DELETE, HTTPS via curl) |
| WebSocket | `rockit.net.ws` | WebSocket client (RFC 6455) |
| URL | `rockit.net.url` | URL parsing, encoding, query parameters |
| Base64 | `rockit.encoding.base64` | Base64 encode/decode |
| XML | `rockit.encoding.xml` | XML parsing and generation |
| DateTime | `rockit.time.datetime` | Date/time, formatting, epoch conversion |
| JSON | `rockit.json` | JSON parse, stringify, pretty-print |
| Probe | `rockit.test.probe` | Test assertions for `@Test` annotated functions |

## Installation

The standard library ships with Rockit. When building the compiler from source, launchpad is included as a git submodule at `RockitCompiler/Stage1/stdlib`.

```bash
git clone --recurse-submodules https://github.com/dark-matter-tech/moon.git
```

## Structure

```
rockit/
├── core/
│   ├── collections.rok    # List map/filter/fold/sort/zip/flatten
│   ├── math.rok           # Integer & float math, trig, constants
│   ├── strings.rok        # pad, repeat, join, split, replace
│   ├── result.rok         # Result type (Success/Failure)
│   └── uuid.rok           # UUID v4 generation
├── encoding/
│   ├── base64.rok         # Base64 encode/decode
│   └── xml.rok            # XML parsing and generation
├── io/
│   ├── file.rok           # File I/O wrappers
│   └── path.rok           # Path join/dir/base/ext/normalize
├── net/
│   ├── http.rok           # HTTP/1.1 client
│   ├── url.rok            # URL parser and encoder
│   └── ws.rok             # WebSocket client (RFC 6455)
├── test/
│   └── probe.rok          # Probe test framework (20 assertions)
├── time/
│   └── datetime.rok       # Date/time utilities
└── json.rok               # JSON encoder/decoder
```

## Contributing

Contributions are welcome. Please open an issue or pull request on [GitHub](https://github.com/dark-matter-tech/launchpad).

## License

Apache 2.0. Copyright 2026 Dark Matter Tech.
