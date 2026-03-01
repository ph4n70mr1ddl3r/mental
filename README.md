# Mental

A cryptographically-verified heads-up poker server implementing mental poker algorithms.

## Overview

Mental delivers mathematically provable fair play for online poker. Using mental poker algorithms, the system guarantees fair shuffles and real-time verification of game integrity—eliminating the possibility of server-side collusion or card manipulation.

## Key Features

- **Trustless Verification**: Players can independently verify game fairness
- **Open-Source Client**: Fully auditable WebAssembly client
- **Heads-Up Only**: 2-player constraint ensures no collusion scenarios
- **Cryptographic Guarantee**: Mathematical proof, not reputation-based trust

## Technology Stack

- **Backend**: C++ server implementing mental poker protocol
- **Frontend**: C++ WebAssembly client with minimal CSS/JS
- **Protocol**: Mental poker algorithm with ZKP proof generation

## Documentation

See [docs/README.md](docs/README.md) for complete documentation including:

- [Product Requirements Document](docs/prd.md)
- [UX Design Specification](docs/ux-design-specification.md)
- [Validation Reports](docs/)

## Project Status

**Implementation Ready** - All documentation is complete, validated, and internally consistent.

## License

MIT
