# Ejemplos de utilización de ENVO API RestFul

### Información general
 
El ENVO API es un servicio que te permite acceder a nuestra plataforma de facturación electrónica, para realizar el envío de comprobantes electrónicos a la DGII.
 
### Funcionalidades principales de nuestra API:

	-Envio de facturas
	-Envio de resumen de facturas
	-Envio de anulaciones de facturas
	
### Recurso/Endpoint

	-Facturas/invoice	
	-Resumen de facturas/resume
	-Anulaciones/canceled
	
Nuestra API está basada en principios REST que harán más fácil tu conexión y desarrollo; métodos HTTP (GET y POST) son utilizados para acceder a los recursos. El sistema procesa el request y retorna un código de respuesta en un formato de fácil compresión.

## Autenticación

### Obtener credenciales de acceso

Debes seguir los siguientes pasos para obtener el token de acceso:

	1.Ingresar a aplicación envo.do
	2.Haz clic sobre el vínculo "Solicitar acceso" en la parte superior y complete el formulario de registro de acceso o vía correo electronico escribiendo a nuestro correo servicios@colladocompania.com.do
	3.Recibira un correo electrónico con las informaciones correspondientes.

### Errores de autenticación

Si el API encuentra algún inconveniente con la autenticación retorna un código 401 y el error encontrado.

## Límite de request

La cantidad de request depende del plan o suscripción adquirida por el cliente.

Si este límite es sobrepasado la aplicación retorna un código 429 ("Too Many request"). Si el usuario llega al límite debe esperar que se termine el período mensualen el cual e encuentre para realizar llamadas al API nuevamente.

## Enviar facturas

`POST /invoice/`

    `curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/invoice`

### Request

	{

	"ECF": {

	  "Encabezado": {

			"Version": "1.0",

	    "IdDoc": [
	      {

		"eNCF": "E310000000002",
		"TipoeCF": 31,
		"FechaVencimientoSecuencia": "31-12-2021",
		"IndicadorNotaCredito": null,
		"IndicadorEnvioDiferido": null,
		"IndicadorMontoGravado": 0,
		"TipoIngresos": 1,
		"TipoPago": 1,
		"FechaLimitePago": null,
		"TerminoPago": null,

		"TablaFormaPago": [
		  {

		    "FormaPago": 1,
		    "MontoPago": 130123

		  },
		  {

		    "FormaPago": 2,
		    "MontoPago": 20123

		  }
		],

		"TipoCuentaPago": null,
		"NumeroCuentaPago": null,
		"BancoPago": null,
		"FechaDesde": null,
		"FechaHasta": null,
		"TotalPaginas": null
	      }
	    ],

	    "Emisor": [
	      {

		"RNCEmisor": "102002959",
		"RazonSocialEmisor": "Envases Antillanos",
		"NombreComercial": "Envases Antiallanos",
		"Sucursal": null,
		"DireccionEmisor": "27 de Febrero, Santiago",
		"Municipio": 20101,
		"Provincia": 20000,

		"TablaTelefonoEmisor": [
		  {

		    "TelefonoEmisor": "809-536-3308",
		    "rnc": null

		  },
		  {

		    "TelefonoEmisor": "809-536-3340",
		    "rnc": null

		  }
		],

		"CorreoEmisor": "envan@en.com",
		"WebSite": "www.envan.com",
		"ActividadEconomica": null,
		"CodigoVendedor": "2012521452",
		"NumeroFacturaInterna": "900001251",
		"NumeroPedidoInterno": "20125214852",
		"ZonaVenta": "Este",
		"RutaVenta": null,
		"InformacionAdicionalEmisor": null,
		"FechaEmision": "27-05-2020"
	      }
	    ],
	    "Comprador": [
	      {
		"RNCComprador": 131978596,
		"IdentificadorExtranjero": null,
		"RazonSocialComprador": "SAP Consulting",
		"ContactoComprador": "William Gonzanlez",
		"CorreoComprador": "plans@hi.com",
		"DireccionComprador": "Av. John F. Kennedy #27",
		"MunicipioComprador": 20101,
		"ProvinciaComprador": 20000,
		"PaisComprador": null,
		"FechaEntrega": "29-05-2020",
		"ContactoEntrega": null,
		"DireccionEntrega": null,
		"TelefonoAdicional": null,
		"FechaOrdenCompra": "25-05-2020",
		"NumeroOrdenCompra": "5014851252",
		"CodigoInternoComprador": "1052142",
		"ResponsablePago": null,
		"Informacionadicionalcomprador": null
	      }
	    ],

	    "InformacionesAdicionales": [
	      {
		"FehcaEmbarque": null,
		"NumeroEmbarque": null,
		"NumeroContenedor": null,
		"NumeroReferencia": null,
		"NombrePuertoEmbarque": null,
		"CondicionesEntrega": null,
		"TotalFOB": null,
		"Seguro": null,
		"Flete": null,
		"OtrosGastos": null,
		"TotalCif": null,
		"RegimenAduanero": null,
		"NombrePuertoSalida": null,
		"NombrePuertoDesembarque": null,
		"PesoBruto": null,
		"PesoNeto": null,
		"UnidadPesoNeto": null,
		"CantidadBulto": null,
		"UnidadBulto": null,
		"VolumenBulto": null,
		"UnidadVolumen": null
	      }
	    ],
	    "Transporte": [
	      {
		"ViaTransporte": null,
		"PaisOrigen": null,
		"DireccionDestino": null,
		"PaisDestino": null,
		"RNCIdentificacionCompaniaTransportista": null,
		"NombreCompaniaTransportista": null,
		"NumeroViaje": null,
		"Conductor": null,
		"DocumentoTransporte": null,
		"Ficha": null,
		"Placa": null,
		"RutaTransporte": null,
		"ZonaTransporte": null,
		"NumeroAlbaran": null
	      }
	    ],
	    "Totales": [
	      {
		"MontoGravadoTotal": 150123,
		"MontoGravadoI1": 150123,
		"MontoGravadoI2": null,
		"MontoGravadoI3": null,
		"MontoExento": null,
		"ITBIS1": 18,
		"ITBIS2": null,
		"ITBIS3": null,
		"TotalITBIS": 12000,
		"TotalITBIS1": 12000,
		"TotalITBIS2": null,
		"TotalITBIS3": null,
		"MontoImpuestoAdicional": null,

		"ImpuestosAdicionales": [
		  {

		    "TipoImpuesto": 1,
		    "TasaImpuestoAdicional": 18,
		    "MontoImpuestoSelectivoConsumoEspecifico": 1200,
		    "MontoImpuestoSelectivoConsumoAdvalorem": 1100,
		    "OtrosImpuestosAdicionales": 0


		  },
		  {

		    "TipoImpuesto": 2,
		    "TasaImpuestoAdicional": 16,
		    "MontoImpuestoSelectivoConsumoEspecifico": 1200,
		    "MontoImpuestoSelectivoConsumoAdvalorem": 1100,
		    "OtrosImpuestosAdicionales": 0


		  }
		],

		"MontoTotal": 130123,
		"MontoNoFacturable": null,
		"MontoPeriodo": null,
		"SaldoAnterior": null,
		"MontoAvancePago": null,
		"ValorPagar": null,
		"TotalITBISRetenido": null,
		"TotalISRRetencion": null,
		"TotalITBISPercepcion": null,
		"TotalISRPercepcion": null
	      }
	    ],
	    "OtraMoneda": [
	      {
		"TipoMoneda": null,
		"TipoCambio": null,
		"MontoGravadoTotalOtraMoneda": null,
		"MontoGravado1OtraMoneda": null,
		"MontoGravado2OtraMoneda": null,
		"MontoGravado3OtraMoneda": null,
		"MontoExentoOtraMoneda": null,
		"TotalITBISOtraMoneda": null,
		"TotalITBIS1OtraMoneda": null,
		"TotalITBIS2OtraMoneda": null,
		"TotalITBIS3OtraMoneda": null,
		"MontoImpuestoAdicionalOtraMoneda": null,

		"ImpuestosAdicionalesOtraMoneda": [
		  {

		    "TipoImpuestoOtraMoneda": 4,
		    "TasaImpuestoOtraMoneda": 10,
		    "MontoImpuestoSelectivoConsumoEspecificoOtraMoneda": 8000,
		    "MontoImpuestoSelectivoConsumoAdvaloremOtraMoneda": 1100,
		    "OtrosImpuestosAdicionalesOtraMoneda": 0

		  },
		  {

		    "TipoImpuestoOtraMoneda": 5,
		    "TisaImpuestoOtraMoneda": 12,
		    "MontoImpuestoSelectivoConsumoEspecificoOtraMoneda": 9500,
		    "MontoImpuestoSelectivoConsumoAdvaloremOtraMoneda": 1100,
		    "OtrosImpuestosAdicionalesOtraMoneda": 0

		  }
		],
		"MontoTotalOtraMoneda": 145000
	      }
	    ]
	  },

	  "DetallesItem": {
	    "Item": [
	      {

		"NumeroLinea": 10,

		"TablaCodigosItem": [
		  {

		    "NumeroLinea": 10,
		    "TipoCodigo": "Producto Termi",
		    "CodigoItem": "C54E122"           

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoCodigo": "Producto Termi",
		    "CodigoItem": "C54E123"           

		  }
		],

		"IndicadorFacturacion": 1,
		"Retencion": [
		  {
		    "IndicadorAgenteRetencionPercepcion": null,
		    "MontoITBISRetenido": null,
		    "MontoISRRetenido": null
		  }
		],

		"NombreItem": "LATAS",
		"IndicadorBienoServicio": 1,
		"DescripcionItem": null,
		"CantidadItem": 5000,
		"UnidadMedida": 20,
		"CantidadReferencia": null,
		"UnidadReferencia": null,

		"TablaSubcantidad": [
		  {

		    "NumeroLinea": 10,
		    "Subcantidad": 50,
		    "CodigoSubcantidad": 2           

		  },
		  {

		    "NumeroLinea": 10,
		    "Subcantidad": 200,
		    "CodigoSubcantidad": 3           

		  }
		],
		"GradosAlcohol": null,
		"PrecioUnitarioReferencia": null,
		"FechaElaboracion": null,
		"FechaVencimiento": null,

		"Mineria": [
		  {
		    "PesoNetoKilogramo": null,
		    "PesoNetoMineria": null,
		    "TipoAfiliacion": null,
		    "Liquidacion": null
		  }
		],
		"PrecioUnitarioItem": 35,
		"DescuentoMonto": null,
		"TablaSubDescuento": [
		  {

		    "NumeroLinea": 10,
		    "TipoSubDescuento": "%",
		    "SubDescuentoPorcentaje": 9.99,
		    "MontoSubdescuento": 3200           

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoSubDescuento": "%",
		    "SubDescuentoPorcentaje": 9.99,
		    "MontoSubdescuento": 1600


		  }
		],
		"RecargoMonto": null,
		"TablaSubRecargo": [
		  {

		    "NumeroLinea": 10,
		    "TipoSubRecargo": "%",
		    "SubRecargoPorcentaje": 9.99,
		    "MontoSubRecargo": 1600

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoSubRecargo": "%",
		    "SubRecargoPorcentaje": 9.99,
		    "MontoSubRecargo": 800

		  }
		],
		"TablaImpuestoAdicional": [
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 2

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 3

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 4

		  }
		],

		"OtraMonedaDetalle": [
		  {
		    "PrecioOtraMoneda": null,
		    "DescuentoOtraMoneda": null,
		    "RecargoOtraMoneda": null,
		    "MontoItemOtraMoneda": null
		  }
		],

		"MontoItem": 5350000

	      },
	      {


		"NumeroLinea": 20,

		"TablaCodigosItem": [
		  {

		    "NumeroLinea": 20,
		    "TipoCodigo": "Producto Termi",
		    "CodigoItem": "C54E122"

		  },
		  {

		    "NumeroLinea": 20,
		    "TipoCodigo": "Producto Termi",
		    "CodigoItem": "C54E123"

		  }
		],

		"IndicadorFacturacion": 1,
		"Retencion": [
		  {
		    "IndicadorAgenteRetencionPercepcion": null,
		    "MontoITBISRetenido": null,
		    "MontoISRRetenido": null
		  }
		],

		"NombreItem": "Laminas",
		"IndicadorBienoServicio": 1,
		"DescripcionItem": null,
		"CantidadItem": 15000,
		"UnidadMedida": 20,
		"CantidadReferencia": null,
		"UnidadReferencia": null,

		"TablaSubcantidad": [
		  {

		    "NumeroLinea": 10,
		    "Subcantidad": 50,
		    "CodigoSubcantidad": 2

		  },
		  {

		    "NumeroLinea": 10,
		    "Subcantidad": 200,
		    "CodigoSubcantidad": 3            

		  }
		],

		"GradosAlcohol": null,
		"PrecioUnitarioReferencia": null,
		"FechaElaboracion": null,
		"FechaVencimiento": null,

		"Mineria": [
		  {
		    "PesoNetoKilogramo": null,
		    "PesoNetoMineria": null,
		    "TipoAfiliacion": null,
		    "Liquidacion": null
		  }
		],

		"PrecioUnitarioItem": 250,
		"DescuentoMonto": null,

		"TablaSubDescuento": [
		  {

		    "NumeroLinea": 10,
		    "TipoSubDescuento": "%",
		    "SubDescuentoPorcentaje": 9.99,
		    "MontoSubdescuento": 3200

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoSubDescuento": "%",
		    "SubDescuentoPorcentaje": 9.99,
		    "MontoSubdescuento": 1600

		  }
		],
		"RecargoMonto": null,
		"TablaSubRecargo": [
		  {

		    "NumeroLinea": 10,
		    "TipoSubRecargo": "%",
		    "SubRecargoPorcentaje": 9.99,
		    "MontoSubRecargo": 1600

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoSubRecargo": "%",
		    "SubRecargoPorcentaje": 9.99,
		    "MontoSubRecargo": 800

		  }
		],
		"TablaImpuestoAdicional": [
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 2

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 3

		  },
		  {

		    "NumeroLinea": 10,
		    "TipoImpuesto": 4

		  }
		],
		"OtraMonedaDetalle": [
		  {
		    "PrecioOtraMoneda": null,
		    "DescuentoOtraMoneda": null,
		    "RecargoOtraMoneda": null,
		    "MontoItemOtraMoneda": null
		  }
		],

		"MontoItem": 9050000

	      }
	    ]
	  },

	  "Subtotales": {
	    "SubTotal": [
	      {        

		"NumeroSubtotal": 1,
		"DescripcionSubtotal": "Sub-total",
		"Orden": 7,
		"SubTotalMontoGravadoTotal": 200,
		"SubTotalMontoGravado1": 1200,
		"SubTotalMontoGravado2": 500,
		"SubTotalMontoGravado3": 350,
		"SubTotalITBIS": 3200,
		"SubTotalITBIS1": 1500,
		"SubTotalITBIS2": 250,
		"SubTotalITBIS3": 0,
		"SubTotalImpuestoAdicional": 520,
		"SubTotalExento": 5500,
		"MontoSubTotal": 12000,
			"Lineas":		  0//ADDED

	      }
	    ]
	  },
	  "DescuentosORecargos": {
	    "DescuentoORecargo": [
	      {

		"NumeroLinea": 10,
		"TipoAjuste": "2",
		"IndicadorNorma1007": 3,
		"DescripcionDescuentoRecargo": "Descuento",
		"TipoValor": "%",
		"ValorDescuentoRecargo": 9.99,
		"MontoDescuentoRecargo": 1580,
		"MontoDescuentoRecargoOtraMoneda": 800,
		"IndicadorFacturacionDescuentoRecargo": 2
	      },
	      {

		"NumeroLinea": 10,
		"TipoAjuste": "2",
		"IndicadorNorma1007": 3,
		"DescripcionDescuentoRecargo": "Recargo",
		"TipoValor": "%",
		"ValorDescuentoRecargo": 9.99,
		"MontoDescuentoRecargo": 1580,
		"MontoDescuentoRecargoOtraMoneda": 500,
		"IndicadorFacturacionDescuentoRecargo": 2

	      }
	    ]
	  },
	  "Paginacion": {
	    "Pagina": [
	      {

		"PaginaNo": 1,
		"NoLineDesde": 2,
		"NoLineHasta": 5200,
		"SubtotalMontoGravadoPagina": 6300,
		"SubtotalMontoGravado1Pagina": 0,
		"SubtotalMontoGravado2Pagina": 120,
		"SubtotalMontoGravado3Pagina": 1580,
		"SubtotalExentoPagina": 500,
		"SubtotalItbisPagina": null,
		"SubtotalItbis1Pagina": 200,
		"SubtotalItbis2Pagina": 1000,
		"SubtotalItbis3Pagina": 0,
		"SubtotalImpuestoAdicionalPagina": 3600,
		"SubtotalImpuestoSelectivoConsumoEspecificoPagina": 0,
		"SubtotalOtroImpuesto": 0,
		"MontoSubtotalPagina": 12300,
		"SubtotalMontoNoFacturablePagina": 12300

	      },
	      {

		"PaginaNo": 2,
		"NoLineDesde": 2,
		"NoLineHasta": 5200,
		"SubtotalMontoGravadoPagina": 6300,
		"SubtotalMontoGravado1Pagina": 0,
		"SubtotalMontoGravado2Pagina": 120,
		"SubtotalMontoGravado3Pagina": 1580,
		"SubtotalExentoPagina": 500,
		"SubtotalItbisPagina": null,
		"SubtotalItbis1Pagina": 200,
		"SubtotalItbis2Pagina": 1000,
		"SubtotalItbis3Pagina": 0,
		"SubtotalImpuestoAdicionalPagina": 3600,
		"SubtotalImpuestoSelectivoConsumoEspecificoPagina": 0,
		"SubtotalOtroImpuesto": 0,
		"MontoSubtotalPagina": 12300,
		"SubtotalMontoNoFacturablePagina": 12300

	      }
	    ]
	  },
	  "InformacionReferencia": [
	    {

	      "NCFModificado": "E310000000000",
	      "RNCOtroContribuyente": 101285142,
	      "FechaNCFModificado": null,
	      "CodigoModificacion": 0,
	      "RazonModificacion": "Cheque Devuelto"

	    }
	  ]
	 }
	}
	
### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Feb 2020 12:36:30 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    []
	
## Resumen de facturas

### Request

`POST /resume/`

    `curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/resume`

	{
	  "RFCE": {
	    "Encabezado": {

	    "version": "1.0",

	    "IdDoc": [

	      {

	    "eNCF": "E320000000003",
	    "TipoeCF": 31,
	    "TipoIngresos": 1,
	    "TipoPago": 1,

	       "TablaFormaPago": [
		    {
		      "FormaPago": 1,
		      "MontoPago": 130123
		    },
		    {
		      "FormaPago": 2,
		      "MontoPago": 20123
		    }
		  ]
		 }
	      ],  

	     "Emisor": [
		{      

		    "RNCEmisor": 102002959,
		    "RazonSocialEmisor": "Envases Antillanos",
		    "FechaEmision": "27-05-2020"

		}
	      ],

	      "Comprador": [
		{

		    "RNCComprador": 102015925,
		    "IdentificadorExtranjero": null,
		    "RazonSocialComprador": "company CXC"
		}
	      ],

	      "Totales": [
		{
		    "MontoGravadoTotal": 150123,
		    "MontoGravadoI1": 150123,
		    "MontoGravadoI2": 12000,
		    "MontoGravadoI3": 12000,
		    "MontoExento": 130123,
		    "TotalITBIS": 1200,
		    "TotalITBIS1": 1300,
		    "TotalITBIS2": 0,
		    "TotalITBIS3": 25000,
		    "MontoImpuestoAdicional": 12300,

			"ImpuestosAdicionales": [
	  {

	    "TipoImpuesto": 1,
	    "MontoImpuestoSelectivoConsumoEspecifico": 1800,
	    "MontoImpuestoSelectivoConsumoAdvalorem": 800,
	    "OtrosImpuestosAdicionales": 500
	  }
	],

		    "MontoTotal": 25000,
		    "MontoNoFacturable": 0,
		    "MontoPeriodo": 0

		}
	      ],
		    "CodigoSeguridadeCF": "ymLKos"
	      }

	  }
	}
	
### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Feb 2020 12:36:30 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    []

## Anulaciones de facturas

### Request

`POST /canceled/`

    `curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/canceled`

	{
	  "ANECF": {
	    "Encabezado": {
	      "version": "1.0",
	      "RNCEmisor": 102002959,
	      "CantidadeNCFAnulados": 2,
	      "FechaHoraAnulacioneNCF": "30-05-2020:10:50:25"
	    },
	    "DetalleAnulacion": {
	      "Anulacion": [
		{
		  "NoLinea": 10,
		  "TipoeCF": 31,
		  "TablaRangoSecuenciasAnuladaseNCF": [
		    {
		      "SecuenciaeNCFDesde": "E310000000001",
		      "SecuenciaeNCFHasta": "E310000000001"
		    }
		  ],
		  "CantidadeNCFAnulados": 2
		}
	      ]
	    }
	  }
	}
	
### Response

    HTTP/1.1 200 OK
    Date: Thu, 24 Feb 2020 12:36:30 GMT
    Status: 200 OK
    Connection: close
    Content-Type: application/json
    Content-Length: 2

    []
    
## Términos y Condiciones ENVO API

Términos y condiciones que debes tener en cuenta al utilizar el API de ENVO.

### Definiciones

	-ENVO API o Servicios ENVO API, hacen referencia a toda la información y funcionalidades que ENVO API dispone en su sitio web y que opera desde el dominio https://app.envo.do

	-Usuario ENVO, toda persona inscrita como Usuario, sea administrador o limitado, en alguna cuenta de ENVO.

	-Desarrollador API, tercero que no disponga de una cuenta en ENVO que tenga acceso a los Servicios ENVO API bajo la autorización de un Usuario ENVO.

	-Usuario ENVO API, todo Usuario ENVO o Desarrollador API que haga uso de los Servicios ENVO API.

	-Las expresiones: ENVO, nosotros, nuestro(a), ENVO Web, hace referencia a Collado & Compañía E.I.R.L

### Términos ENVO API

Los términos y condiciones del servicio ENVO API son complementarios a los términos y condiciones de la aplicación ENVO.

Los términos y condiciones que hacen parte de esta sección aplican a cualquier uso de ENVO API por parte de:

Usuarios ENVO y Desarrolladores u operadores de sitios web o aplicaciones (Desarrollador API), quienes bajo la autorización de un Usuario ENVO tengan acceso a ENVO API.
Toda funcionalidad o implementación desarrollada a través de ENVO API (Implementación ENVO API) se encuentra sujeta a los términos presentes en esta publicación.

El servicio ENVO API está disponible para todos nuestros planes de suscripciones. El uso de ENVO API no tiene ningún costo adicional al valor del plan en el que esté suscrito el ciente. ENVO se reserva el derecho de modificar las tarifas para este servicio; en caso que haya un cambio Collado & Compañía, Division ENVO notificará a sus clientes con anticipación.

Si eres un Usuario ENVO y permites que un tercero (Desarrollador API) desarrolle una Implementación ENVO API para tu uso; estos términos aplican a dicho tercero y para el cliente, además usted como usuario es responsable del cumplimiento de ambas partes por las políticas de esta sección.

ENVO asegura la protección de tu información en nuestro servicio ENVO API, en el caso que quieras permitir el acceso a tus datos por parte de un Desarrollador API, asumes la responsabilidad por cualquier uso que se haga con esta información. ENVO no tiene ninguna clase de responsabilidad sobre el uso de los datos posterior a tu aprobación de compartirlos.

Al hacer uso de ENVO API, ya sea como Usuario ENVO o Desarrollador API, aceptas y muestras conformidad con los términos presentes en esta publicación. ENVO puede modificar sin previo aviso estos términos. El uso de los servicios ENVO API posterior a la publicación de los nuevos términos constituye tu aceptación de los mismos. Si no estás de acuerdo con los nuevos Términos debes suspender el uso de los servicios ENVO API.

ENVO concede una licencia o acceso limitado, revocable, no exclusiva, no susceptible de sublicenciar y sujeta a los Términos para el uso de ENVO API. Toda distribución o comercialización de cualquier producto o servicio desarrollado a través de ENVO API, debe ser autorizada previamente por ENVO quien se reserva la decisión de aceptarla o no.

Al hacer uso de los servicios ENVO API te encuentras sujeto a las siguientes restricciones. 

No podrás:

	-Interferir con el correcto funcionamiento de ENVO API o distribuir cualquier Implementación ENVO API que afecte negativamente los servicios ENVO u otra aplicación que use ENVO API.
	-Usar las credenciales de otro Usuario ENVO o Desarrollador API.
	-Ocultar a ENVO información sobre tu uso de ENVO API.
	-Usar ENVO API en asociación o como contenido en sitios web o aplicaciones que en el criterio de ENVO sean considerados obscenos o inapropiados.
	-Utilizar ENVO API en aplicaciones que contengan, promuevan o estén conectadas con spyware, adware u otros códigos o programas maliciosos.
	-Usar ENVO API en ninguna forma o para ningún propósito que viole la ley o los derechos de un individuo.
	-Intentar extraer o copiar información del código base o de Usuarios ENVO.
	-Difamar o representar negativamente a ENVO en tu Implementación de ENVO API.
	-Usar ENVO API para cualquier uso que intente reemplazar o replicar la experiencia de uso o la funcionalidad de ENVO.
	-Desarrollar una Implementación ENVO API, producto o servicio que en consideración de ENVO represente competencia.
	-Hacer esfuerzos o actos que tengan como fin persuadir a los Usuarios ENVO de cancelar el servicio.
	-Desarrollar cualquier Implementación ENVO API que a nuestro juicio se oponga o vaya en contravía de los principios y objetivos de ENVO.
	-Al utilizar ENVO API, reconoces y permites que ENVO establezca o modifique el número máximo de peticiones que puedes realizar a través de nuestros servicios, los límites vigentes de uso para ENVO API los puedes encontrar en documento Límite de request. En caso que haya un cambio en estos valores, serás notificado con anterioridad.

ENVO podrá monitorear en cualquier momento tu uso de ENVO API con el fin de asegurar el cumplimiento de estos términos, no debes interferir u ocultar información a ENVO durante este proceso.

Al acceder a los servicios ENVO API, aceptas que el uso por parte de ENVO de cualquier Implementación ENVO API desarrollada por ti, no constituye nuestra aceptación de los términos que se requieran para su uso.

ENVO se reserva el derecho de cancelar, bloquear y prohibir sin previa notificación el uso de ENVO API a cualquier Usuario ENVO o Desarrollador API que consideremos incumple o viola los términos descritos en esta sección.
