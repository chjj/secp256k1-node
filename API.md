# API Reference (v3.x)

- [`.privateKeyVerify(Buffer privateKey)`](#privatekeyverifybuffer-privatekey---boolean)
- [`.privateKeyExport(Buffer privateKey [, Boolean compressed = true])`](#privatekeyexportbuffer-privatekey--boolean-compressed--true---buffer)
- [`.privateKeyImport(Buffer privateKey)`](#privatekeyimportbuffer-privatekey---buffer)
- [`.privateKeyTweakAdd(Buffer privateKey, Buffer tweak)`](#privatekeytweakaddbuffer-privatekey-buffer-tweak---buffer)
- [`.privateKeyTweakMul(Buffer privateKey, Buffer tweak)`](#privatekeytweakmulbuffer-privatekey-buffer-tweak---buffer)
- [`.publicKeyCreate(Buffer privateKey [, Boolean compressed = true])`](#publickeycreatebuffer-privatekey--boolean-compressed--true---buffer)
- [`.publicKeyConvert(Buffer publicKey [, Boolean compressed = true])`](#publickeyconvertbuffer-publickey--boolean-compressed--true---buffer)
- [`.publicKeyVerify(Buffer publicKey)`](#publickeyverifybuffer-publickey---boolean)
- [`.publicKeyTweakAdd(Buffer publicKey, Buffer tweak [, Boolean compressed = true])`](#publickeytweakaddbuffer-publickey-buffer-tweak--boolean-compressed--true---buffer)
- [`.publicKeyTweakMul(Buffer publicKey, Buffer tweak [, Boolean compressed = true])`](#publickeytweakmulbuffer-publickey-buffer-tweak--boolean-compressed--true---buffer)
- [`.publicKeyCombine(Array<Buffer> publicKeys [, Boolean compressed = true])`](#publickeycombinearraybuffer-publickeys--boolean-compressed--true---buffer)
- [`.signatureNormalize(Buffer signature)`](#signaturenormalizebuffer-signature---buffer)
- [`.signatureExport(Buffer signature)`](#signatureexportbuffer-signature---buffer)
- [`.signatureImport(Buffer signature)`](#signatureimportbuffer-signature---buffer)
- [`.sign(Buffer message, Buffer privateKey [, Object options])`](#signbuffer-message-buffer-privatekey--object-options---signature-buffer-recovery-number)
  - [Option: `Function noncefn`](#option-function-noncefn)
  - [Option: `Buffer data`](#option-buffer-data)
- [`.verify(Buffer message, Buffer signature, Buffer publicKey)`](#verifybuffer-message-buffer-signature-buffer-publickey---boolean)
- [`.recover(Buffer message, Buffer signature, Number recovery [, Boolean compressed = true])`](#recoverbuffer-message-buffer-signature-number-recovery--boolean-compressed--true---buffer)
- [`.ecdh(Buffer publicKey, Buffer privateKey)`](#ecdhbuffer-publickey-buffer-privatekey---buffer)
- [`.ecdhUnsafe(Buffer publicKey, Buffer privateKey [, Boolean compressed = true])`](#ecdhunsafebuffer-publickey-buffer-privatekey--boolean-compressed--true---buffer)

#####`.privateKeyVerify(Buffer privateKey)` -> `Boolean`

Verify an ECDSA *privateKey*.

<hr>

#####`.privateKeyExport(Buffer privateKey [, Boolean compressed = true])` -> `Buffer`

Export a *privateKey* in DER format.

<hr>

#####`.privateKeyImport(Buffer privateKey)` -> `Buffer`

Import a *privateKey* in DER format.

<hr>

#####`.privateKeyTweakAdd(Buffer privateKey, Buffer tweak)` -> `Buffer`

Tweak a *privateKey* by adding *tweak* to it.

<hr>

#####`.privateKeyTweakMul(Buffer privateKey, Buffer tweak)` -> `Buffer`

Tweak a *privateKey* by multiplying it by a *tweak*.

<hr>

#####`.publicKeyCreate(Buffer privateKey [, Boolean compressed = true])` -> `Buffer`

Compute the public key for a *privateKey*.

<hr>

#####`.publicKeyConvert(Buffer publicKey [, Boolean compressed = true])` -> `Buffer`

Convert a *publicKey* to *compressed* or *uncompressed* form.

<hr>

#####`.publicKeyVerify(Buffer publicKey)` -> `Boolean`

Verify an ECDSA *publicKey*.

<hr>

#####`.publicKeyTweakAdd(Buffer publicKey, Buffer tweak [, Boolean compressed = true])` -> `Buffer`

Tweak a *publicKey* by adding *tweak* times the generator to it.

<hr>

#####`.publicKeyTweakMul(Buffer publicKey, Buffer tweak [, Boolean compressed = true])` -> `Buffer`

Tweak a *publicKey* by multiplying it by a *tweak* value.

<hr>

#####`.publicKeyCombine(Array<Buffer> publicKeys [, Boolean compressed = true])` -> `Buffer`

Add a given *publicKeys* together.

<hr>

#####`.signatureNormalize(Buffer signature)` -> `Buffer`

Convert a *signature* to a normalized lower-S form.

<hr>

#####`.signatureExport(Buffer signature)` -> `Buffer`

Serialize an ECDSA *signature* in DER format.

<hr>

#####`.signatureImport(Buffer signature)` -> `Buffer`

Parse a DER ECDSA *signature*.

<hr>

#####`.sign(Buffer message, Buffer privateKey [, Object options])` -> `{signature: Buffer, recovery: number}`

Create an ECDSA signature. Always return low-S signature.

######Option: `Function noncefn`

Nonce generator. By default it is [rfc6979](https://tools.ietf.org/html/rfc6979).

Function signature: `noncefn(Buffer message, Buffer privateKey, ?Buffer algo, ?Buffer data, Number attempt)` -> `Buffer`

######Option: `Buffer data`

Additional data for [noncefn](#option-function-noncefn) (RFC 6979 3.6) (32 bytes). By default is `null`.

<hr>

#####`.verify(Buffer message, Buffer signature, Buffer publicKey)` -> `Boolean`

Verify an ECDSA signature.

Note: **return false for high signatures!**

<hr>

#####`.recover(Buffer message, Buffer signature, Number recovery [, Boolean compressed = true])` -> `Buffer`

Recover an ECDSA public key from a signature.

<hr>

#####`.ecdh(Buffer publicKey, Buffer privateKey)` -> `Buffer`

Compute an EC Diffie-Hellman secret and applied sha256 to compressed public key.

<hr>

#####`.ecdhUnsafe(Buffer publicKey, Buffer privateKey [, Boolean compressed = true])` -> `Buffer`

Compute an EC Diffie-Hellman secret and return public key as result.
