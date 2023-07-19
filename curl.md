# CURL

## Proxy
```
curl -x http://USER:PASSWD@PROXY_SERVER:PROXY_PORT -L -X POST 'http://url'
```

## Certificado

### Extrai a chave e o certificado de um P12
openssl pkcs12 -in certificado.p12 -out file.key -nocerts -legacy -nodes
openssl pkcs12 -in certificado.p12 -out file.crt -clcerts -legacy -nokeys

```
curl -k -X POST -E ./file.crt --key ./file.key "URL"
```

### Token
Instalar
```
sudo apt install gnutls-bin libengine-pkcs11-openssl
```

Rodar o comando: 
```
p11tool --list-tokens
```

Ele vai devolver alguns dados do token. Pegar o q vem no campo URL do retorno acima

```
curl -v -k -X 'GET' -E 'pkcs11\:model=??;manufacturer=??;serial=??;token=??' 'URL'
```

Obs.:
- colocar uma "\" antes dos dois pontos
- trocar os caracteres que vieram codificados como o espaço veio com %20 e a vírgula com "%2C"
