# OCK Rotor — key material

OCK Rotor v0.4 accepts two key families.

## Integer keys

Direct:

    --key-ints "233969659 753251273 593294788 325244558 296780300 467383710"

From a file:

    --key-int-file ints.key

The same integer sequence is required for decode.

## Word keys

Direct:

    --dict okc.dict --key-words "luna pariah funk vibrates"

From a phrase file:

    --dict okc.dict --key-word-file phrase.words

Word mode resolves the words through the supplied dictionary.
Decode therefore requires compatible dictionary + word material.

## What OCKR4 stores

The OCKR4 container stores the parameters required to replay the transform:

- magic/version
- nonce
- round count
- rotor count
- ciphertext
- 32-byte toy authentication tag

The secret integer/word key material is not embedded as plaintext key material.

## Key handling

Treat key files as secrets when they are used for anything beyond demos.

For password-manager integration, the preferred future interface is `--key-stdin`,
so a secret can be piped into the process without appearing in shell history.

The current cipher is educational and unaudited.
