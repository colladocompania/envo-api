# Ejemplos de utilización de ENVO API RestFul

Explicación en detalle para consumir el API

The entire application is contained within the `app.rb` file.

`config.ru` is a minimal Rack configuration for unicorn.

`run-tests.sh` runs a simplistic test and generates the API
documentation below.

It uses `run-curl-tests.rb` which runs each command defined in
`commands.yml`.

## Información general

Esta página te ayudará a comenzar con el API ENVO
 
El API ENVO es un servicio que te permite acceder a nuestra plataforma de facturación electronica, para realizar el envio de comprobantes electronicos a la DGII.
 
Funcionalidades principales de nuestra API:

-Envio de facturas
-Envio de resumen de facturas
-Envio de anulaciones de facturas
