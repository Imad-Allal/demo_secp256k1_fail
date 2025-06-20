# demo_secp256k1_implementation

This repository showcases an error happening with `secp256k1` when generating solidity verifiers using `Barretenberg`, in the case where we hardcode the public keys of the signers in the circuit.

## How to run

1. **Clone the repository**

```bash
git clone https://github.com/Imad-Allal/demo_secp256k1_fail
```

2. **Run tests**

    Tests pass for both cases

```bash
cd correct_implementation
nargo test
```

```bash
cd wrong_implementation
nargo test
```

3. **Generate the solidity verifier**

    For both implementations, we use `Barretenberg` and `nargo` to generate the solidity verifier. The only difference is that in the `correct_implementation`, we pass the signer public keys as parameters of the `main` function, while in the `wrong_implementation`, we hardcode them in the circuit.

```bash
cd correct_implementation
nargo execute
bb write_vk -b target/working_secp256k1.json -o target --oracle_hash keccak
```

```bash
cd wrong_implementation
nargo execute
bb write_vk -b target/failing_secp256k1.json -o target --oracle_hash keccak
```

## Additional information

```bash
╰─❯ nargo --version
nargo version = 1.0.0-beta.6
noirc version = 1.0.0-beta.6+e796dfd67726cbc28eb9991782533b211025928d
(git version hash: e796dfd67726cbc28eb9991782533b211025928d, is dirty: false)
```

```bash
╰─❯ bb --version                                                               
0.84.0
```
