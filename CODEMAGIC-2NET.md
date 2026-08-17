# Codemagic — 2NET Rastreamento

## Android

No Codemagic, em **Team settings → codemagic.yaml settings → Code signing identities → Android keystores**, envie o keystore da 2NET e use como referência:

`2net_android_keystore`

O mesmo keystore deve ser preservado para todas as futuras versões publicadas na Google Play.

## iOS

O workflow usa:

`org.traccar.client.TraccarClient`

nesta primeira etapa porque o projeto original ainda usa o Bundle ID/Firebase do Traccar.

Antes da publicação da 2NET, crie o Bundle ID definitivo, por exemplo:

`br.com.2net.rastreamento`

Depois crie um novo projeto Firebase para a 2NET e substitua:

- `android/app/google-services.json`
- `ios/Runner/GoogleService-Info.plist`

No Codemagic, configure a assinatura iOS para o Bundle ID definitivo.

## Primeiro teste

Recomendo executar primeiro:

`android-2net-unsigned-test`

Depois:

`android-2net`

E somente após o Android estar funcionando, configurar o workflow iOS.

## Importante

O `codemagic.yaml` precisa ficar na raiz do repositório GitHub.
