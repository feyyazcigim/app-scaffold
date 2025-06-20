# Hyli App Scaffold

This repository provides a scaffold to build applications on the Hyli network using Risc0 contracts.

## Architecture

The application follows a client-server model:

- The frontend sends operation requests to the server.
- The server handles transaction creation, proving, and submission.
- All interactions are executed through the Hyli network.

Currently, only Risc0 contracts are supported.

## Getting Started

### Pre-requisites

- Clone [the Hyli node repository](github.com/hyli-org/hyli)
- Clone this repository
- [Install RISC-Zero](https://dev.risczero.com/api/zkvm/install)
- [Install Docker](https://docs.docker.com/compose/install/)

### 1. Start the Hyli node

You can run the docker node and the wallet using

```bash
docker-compose up -d
```

This will launch a development-mode node and the wallet server and ui.

### 2. Start the server

From the root of this repository:

```bash
RISC0_DEV_MODE=1 cargo run -p server
```

This starts the backend service, which handles contract interactions and proofs.

### 3. Start the frontend

To navigate to the frontend directory and start the development server:

```bash
cd front
bun install
bun run dev
```

This runs the web interface for interacting with the Hyli network.

## Development

### Building Contracts

Contract ELF files are rebuilt automatically when changes are made.

For reproducible builds using Docker:

```bash
cargo build -p contracts --features build --features all
```

This ensures builds are consistent across environments.

If you want to build in non-reproducible mode (to test contract compilation):
```bash
cargo build -p contracts --features build --features all --features nonreproducible
```

For more details, refer to the [Hyli documentation](https://docs.hyli.org).
