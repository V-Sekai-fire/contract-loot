# contract-loot

The loot core: seeded weighted drops and first-touch contention, specified in Lean and emitted as a GPU kernel that matches it bit for bit.

## What it is for

The core is a pure reducer with no dependencies, and narrow C ports in `repository/` connect it to adapters for the engine, the wire and recorded fixtures. The roll is authored once in Lean and lowered through Slang to SPIR-V, and a parity runner checks the GPU output against golden vectors the Lean side writes. A 128-bit fixed-point multiply takes the same path and is checked against the host's C implementation. RFD 2028 owns the core, ports and adapters layout, and RFD 2045 the loot-action loop.

## Build and run

    cd core && lake exe loot_demo

The `Containerfile` builds an image that runs the GPU parity check on a software renderer.

## Licence

MIT. See [LICENSE](LICENSE).
