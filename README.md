# Ejemplos de utilización de ENVO API RestFul

## Información general
 
El API ENVO es un servicio que te permite acceder a nuestra plataforma de facturación electrónica, para realizar el envío de comprobantes electrónicos a la DGII.
 
### Funcionalidades principales de nuestra API:

	-Envio de facturas
	-Envio de resumen de facturas
	-Envio de anulaciones de facturas
	
### Recurso/Endpoint

	1.Facturas/invoice	
	2.Resumen de facturas/resume
	3.Anulaciones/canceled
	
Nuestra API está basada en principios REST que harán más fácil tu conexión y desarrollo; métodos HTTP (GET y POST) son utilizados para acceder a los recursos. El sistema    	 procesa el request y retorna un código de respuesta en un formato de fácil compresión.

## Enviar facturas

`POST /invoice/`

    curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/invoice

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
		"RNCComprador": 101896183,
		"IdentificadorExtranjero": null,
		"RazonSocialComprador": "SAP Consulting",
		"ContactoComprador": "William Gonzanlez",
		"CorreoComprador": "dts@hi.com",
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
		    "TasaImpuestoAdicional": 16,
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

    curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/resume

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

## Anulaciones

### Request

`POST /canceled/`

    curl -i -H 'Accept: application/json' -d '' https://app.envo.do/invoices/api/canceled

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
		      "SecuenciaeNCFHasta": "E310000000002"
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
