# POLY 3

## Zero-Knowledge Proof Verification Project

This repository contains the implementation and deployment instructions for a zero-knowledge proof (ZKP) verification project. The project includes:

- A circom circuit implementation (`circuit.circom`) for a specific proof scenario.
- Instructions to compile the circom circuit and generate circuit intermediaries.
- Deployment of a Solidity verifier contract (`Verifier.sol`) to Sepolia or Mumbai Testnet.
- Verification of a generated proof using the deployed verifier contract.

## Table of Contents

1. [Circuit Implementation](#circuit-implementation)
2. [Compiling the Circuit](#compiling-the-circuit)
3. [Generating a Proof](#generating-a-proof)
4. [Deploying the Verifier Contract](#deploying-the-verifier-contract)
5. [Verifying the Proof](#verifying-the-proof)
6. [Contributing](#contributing)
7. [License](#license)

## 1. Circuit Implementation

The circuit (`circuit.circom`) implements a specific zero-knowledge proof scenario where inputs A and B are used to prove a statement.

## 2. Compiling the Circuit

To compile the circom circuit and generate circuit intermediaries:

```bash
npx circom circuit.circom -o circuit
```

This command compiles `circuit.circom` and outputs the circuit files to the `circuit/` directory.

## 3. Generating a Proof

After compiling the circuit, generate a proof using specific inputs, for example, A=0 and B=1:

```bash
npx snarkjs wtns calculate circuit.wasm input.json witness.wtns
npx snarkjs groth16 prove circuit_final.zkey input.json witness.wtns proof.json public.json
```

Adjust `input.json` to match the inputs required by your circuit.

## 4. Deploying the Verifier Contract

Deploy the Solidity verifier contract (`Verifier.sol`) to Sepolia or Mumbai Testnet:

```bash
# Compile Verifier.sol using your preferred Solidity compiler
# Deploy using Hardhat, Truffle, or Remix IDE to Sepolia or Mumbai Testnet
```

Ensure to configure your deployment script with correct network configurations and verify contract addresses.

## 5. Verifying the Proof

After deploying the verifier contract, call the `verifyProof()` method with the generated proof:

```javascript
// Example using ethers.js
const verifier = await ethers.getContractAt('Verifier', verifierContractAddress);
const isProofValid = await verifier.verifyProof(proof, inputs);

console.log("Proof verification result:", isProofValid);
```

Ensure `proof` and `inputs` are correctly formatted according to the verifier contract's specifications. Assert that `isProofValid` evaluates to `true` to confirm successful proof verification.

## 6. Contributing

Contributions are welcome! Please fork this repository and submit pull requests to propose improvements or fixes.

## 7. License

This project is licensed under the [MIT License](LICENSE).

---

Feel free to adapt the instructions and commands based on your specific implementation details and tooling preferences. Good luck with your ZKP verification project!
