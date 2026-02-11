# svca-inescapavel

## O que `build.sh` faz

* Compila `src/module.go` para WASM com flags determinísticas:
  * `GOOS=js`
  * `GOARCH=wasm`
  * `-trimpath`
  * `-buildid=`
* Gera `manifest.sha256`
* Gera `manifest.json` estático (sem timestamp)
* Assina o manifesto usando chave Ed25519 **já versionada**
* Nunca gera ou sobrescreve chave pública
* Não acessa rede
* Não depende de data/hora

⚠️ O repositório contém a chave pública estável (`capsule/pubkey.pem`).  
A chave privada não é versionada.

## Determinismo Formal

Se dois usuários executarem:

```bash
./build.sh
sha256sum build/module.wasm build/manifest.sha256 build/signature.bin
```

Os hashes serão idênticos.

O CI valida isso automaticamente com dois builds consecutivos e compara os hashes dos artefatos assinados.
