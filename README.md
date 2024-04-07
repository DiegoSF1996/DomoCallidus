
# Domo Callidus

Trabalho de conclusão de curso de engenharia elétrica da faculdade Dom Pedro II.
Este trabalho serve de base para qualquer pessoa que queira construir um sistema automatizado.

A presente aplicação permite acender e apagar uma lâmpada  por meio de um aplicativo para android.
O App e o ESP32 devem estar conectados a mesma rede wifi para que a comunicação ocorra.
O Acionamento da lâmpada ocorre no seguinte fluxo:
- Usuário aciona botão no app
- app envia comando para ip do esp32 atraves do wifi
- esp32 recebe sinal e aciona o rele permitindo a tensão da rede elétrica fluir para a lâmpada.



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
Foi utilizado a IDE do arduino para programar e gravar o software no ESP32
