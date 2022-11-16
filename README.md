
# Título do Projeto

Trabalho de conclusão de curso da faculdade Dom Pedro II, curso de engenharia elétrica.
Este trabalho serve de base para qualquer pessoas que queira construir um sistema automatizado.



## NativeScript

## Documentação da API

#### Gera a keystore

```bash
  keytool -genkey -v -keystore my-release-key.keystore -alias DomoCallidus -keyalg RSA -keysize 2048 -validity 10000

```

#### Gera uma release do app
```bash
  ns build android --release --key-store-path C:\keystore\NativeScriptApp.keystore --key-store-password 12345678 --key-store-alias DomoCallidus --key-store-alias-password 12345678
```

## ESP32