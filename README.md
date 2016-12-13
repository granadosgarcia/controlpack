# Control-pack API

## Contenido

- Uso
- Endpoints


## Uso
Puntos clave de la API para poder cotizar y ordenar:

- se necesita un apikey

## GET /preorder/?delivery=LAT,LON&pickup=LAT,LON

Aquí se cotiza y se ve la disponibilidad de una entrega entres los dos puntos que se entregan en el query 
 

__Ejemplo de uso:__
 
[**/api/v1/preorder/?delivery=19.4376401,-99.1758606&pickup=19.4376401,-99.1758606**]()

Se cotiza un envío del angel de la independencia a la fuente de la cibeles  

**Respuesta:**
<pre>
{
    "preorder": {
    	"id": 1022, //INT numero de preorden
		"possible": True, //BOOLEAN sobre si se puede completar
		"cost": 25,000, //INT de centavos mexicanos
		"eta": 19, //INT de minutos
    }
}
</pre>

## GET /order/?preorder=PREORDERID&phone=NUM&name=NOMBRE&address=DIRECCION


Aquí se hace el pedido a partir de un id de preorden ya realizado 

__Ejemplo de uso:__
 
[**/api/v1/order/?preorder=1022&phone=222123123&name=Kevin%20Perez&address=Colima12**]()

Se confirma un envío del angel de la independencia a la fuente de la cibeles con el id 1022 

**Respuesta:**
<pre>
{
    "order": {
    	"status": Processing, //STRING with the status of the order
    	"id": 2, //INT numero de orden
    	"cost": 25,000, //INT de centavos mexicanos
		"orderDate": 2017-04-17T02:00:00.000Z, //Date en que se pidió
		"pickupDate": 2017-04-17T02:10:00.000Z, //Date en que se recogió
		"deliveryDate": 2017-04-17T02:20:00.000Z, //Date en que se entregó
		"estimatedArrival": 2017-04-17T02:18:00.000Z //Date estimada entrega
		"currently": "19.4376401,-99.1758606", //String with live coordinates
		"clientPhone": 222123123, //INT with phone number
		"clientName": "Kevin Perez", //INT with phone number
		"clientAddress": "Colima 12" //STRING with address
    }
}
</pre>

## GET /order/?delivery=LAT,LON&pickup=LAT,LON&phone=NUM&name=NOMBRE&address=DIRECCION


Aquí se hace el pedido a partir de un par de puntos sin haber preordenado  

__Ejemplo de uso:__
 
[**/api/v1/order/?preorder=1022&phone=222123123&name=Kevin%20Perez&address=Colima12**]()

Se confirma un envío del angel de la independencia a la fuente de la cibeles con el id 1022 

**Respuesta:**
<pre>
{
    "order": {
    	"status": Processing, //STRING with the status of the order
    	"id": 2, //INT numero de orden
    	"cost": 25,000, //INT de centavos mexicanos
		"orderDate": 2017-04-17T02:00:00.000Z, //Date en que se pidió
		"pickupDate": 2017-04-17T02:10:00.000Z, //Date en que se recogió
		"deliveryDate": 2017-04-17T02:20:00.000Z, //Date en que se entregó
		"estimatedArrival": 2017-04-17T02:18:00.000Z //Date estimada entrega
		"currently": "19.4376401,-99.1758606", //String with live coordinates
		"clientPhone": 222123123, //INT with phone number
		"clientName": "Kevin Perez", //STRING with phone number
		"clientAddress": "Colima 12" //STRING with address
    }
}
</pre>



