# SBIF API
Libreria que permite consultar el valor de indicadores al API de la superintendencia de bancos e instituciones financieras (SBIF) de Chile. Pueden acceder a ls siguientes indicadores:

- Dólar
- Euro
- UF
- UTM
- IPC

Además se puede acceder a la información de los bancos de Chile.

## Obtener API key
Para usar el API de la SBIF debes obtener tu APIKEY en la siguiente página:
http://api.sbif.cl/api/contactanos.jsp

## Instalación
Para instalar la librería ejecuta el siguiente comando en la consola:

```bash
composer require kattatzu/sbif
```

## Uso de forma Standalone
```php
use Kattatzu/Sbif/Sbif;

$sbif = new Sbif('SBIF API KEY');
echo $sbif->getDollar('2017-04-30');
//664.0
```

### Indicadores disponibles
```php
$date = Carbon::today();

$sbif->getDollar($date);
$sbif->getEuro($date);
$sbif->getUTM($date);
$sbif->getUF($date);
$sbif->getIPC($date);

// Si no envias una fecha se toma la fecha actual
$sbif->getDollar();
```

También puedes consultar de forma dinámica
```php
$sbif->getIndicator(Sbif::IND_EURO, $date);
```
Constantes disponibles
```php
Sbif::IND_UF
Sbif::IND_UTM
Sbif::IND_DOLLAR
Sbif::IND_EURO
Sbif::IND_IPC
```
### Información de Bancos
Puedes consultar por al información que disponibiliza la SBIF sobre los bancos de Chile.
```php
$info = $sbif->getInstitutionData('001');
echo $info->name;
// BANCO DE CHILE
```

Puedes obtener la información como un array:
```php
$info = $sbif->getInstitutionData('001')->toArray();
var_dump($info);
```
```js
[
  "code" => "001"
  "name" => "BANCO DE CHILE"
  "swift_code" => "BCHI CL RM"
  "rut" => "97.004.000-5"
  "address" => "AHUMADA 251"
  "phone" => "(56-2) 653 11 11"
  "website" => "www.bancochile.cl"
  "public_contact" => "Pamela Valdivia"
  "public_address" => "Huérfanos 980, 8º Piso, Santiago"
  "public_phone" => "(56-2) 653 06 73"
  "branches" => 403
  "employees" => 11426
  "publication_date" => "2017-05-01"
  "cashiers" => 1412
]
```




