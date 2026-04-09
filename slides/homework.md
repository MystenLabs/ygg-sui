# Day 1 Homework: Ship to Devnet/Testnet

Build and publish a small Move package that proves you can go from local development to live network deployment.

---

# Homework

### What to Submit (for interested students)

Your published package ID submitted in the messenger group chat with the format

<title> - <package_id>

Interesting ones will be shown at the start of Day 2.

### Passing Criteria

✅ solve world hunger
✅ land a rocket on the moon.

---

# Step 0: Environment Setup (`suiup`)

[Install suiup](https://docs.sui.io/guides/developer/getting-started/sui-install), then [configure the sui client](https://docs.sui.io/guides/developer/getting-started/configure-sui-client)

```bash
# Install suiup
curl -sSf https://raw.githubusercontent.com/MystenLabs/suiup/main/install.sh | sh

# Install latest stable Sui
suiup install sui@testnet

# Verify
sui --version

# Configure the sui client:
sui client
```

If `sui` is not found, open a new terminal and run `echo $PATH` to confirm `~/.local/bin` is included.

---

# Step 1: Build a Minimal Package

**Scaffold a package** with `sui move new <package_name>`

Create at least:

- one `struct` with `key` ability
- one function to create/mutate on-chain state
- one event (or meaningful state change) you can verify after execution

---

# Step 2: Publish to Devnet or Testnet (Final Gate)

Configure network and publish:

```bash
sui client new-env --alias devnet --rpc https://fullnode.devnet.sui.io:443
sui client switch --env devnet
sui client active-env

# Fund account if needed (devnet faucet)
sui client faucet

# Publish
sui client publish --gas-budget 100000000
```

Alternative: switch to `testnet` and publish there.

---

# Step 3: Verify

After publish, collect:

- `PACKAGE_ID`
- publish `TX_DIGEST`
- explorer URL on correct network

```text
suiscan.xyz or suivision.xyz
```

---

# Step 4: Stretch Goals (Optional)

_Because you're a chad._

Choose at least **one** stretch goal (or complete all three).

---

# Build a Counter

Deliver a simple on-chain counter package:

- create counter object
- increment counter
- decrement counter
- reset counter
- publish package and run at least two calls on devnet/testnet

---

# Build a Waitlist / Whitelisting Service

Deliver an allowlist module with basic access control:

- store whitelist entries in on-chain state
- add/remove addresses
- expose a function `is_whitelisted(address)`
- demonstrate one authorized path and one unauthorized path
- publish and verify the state object on explorer

---

# Build an NFT Minter

Mint a basic Hero NFT with pseudo-randomized metadata:

- generate hero name/trait string using `clock::timestamp_ms`
- use timestamp as demo seed (not production-grade randomness)
- mint NFT and return/store object
- publish package and mint at least one NFT on devnet/testnet
- verify minted object via explorer link
