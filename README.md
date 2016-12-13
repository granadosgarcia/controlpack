# Control-pack API

REST API de control-pack con la que se pueden cotizar ordenes y confirmarlas

## Contenido

- Uso
- Endpoints


# Uso

Puntos clave de la API para poder cotizar y ordenar

-----

# Endpoints


## GET /orders/

Listar todas las ordenes realizadas por la cuenta


 ----

__Ejemplo de uso:__
 
[**https://controlpack.com/api/v1/orders**]()


----
**Respuesta:**
<pre>
{
	"orders": [
		{
			 "order": {
		    	"id": 1022, //INT numero de preorden
				"possible": True, //BOOLEAN sobre si se puede completar
				"cost": 25000, //INT de centavos mexicanos
				"eta": 19, //INT de minutos
			}
	    },
		{
			 "order": {
		    	"id": 1023, //INT numero de preorden
				"possible": True, //BOOLEAN sobre si se puede completar
				"cost": 35000, //INT de centavos mexicanos
				"eta": 11, //INT de minutos
			}
	    }
	]
}
</pre>

## POST /orders/

Se crea una nueva orden 


| Argumento     | Descripción   | 
| ------------- |:-------------| 
| delivery      | Un objeto con el par de puntos de latitud y longitud donde se entrega. La latitud debe estar entre -90 y 90 inclusivos y la longitud -180 y 180. Ejemplo: <br> { <br>	 "delivery": <br> { "lat": 37.71283, "long": -122.13901}<br>} | 
| pickup	      |  Un objeto con el par de puntos de latitud y longitud donde se recoge el pedido. La latitud debe estar entre -90 y 90 inclusivos y la longitud -180 y 180. Ejemplo: <br> { <br>	 "pickup": <br> { "lat": 37.71283, "long": -122.13901}<br>}       |
| clientPhone | El número de telefono del cliente. Ejemplo: <br> 223232333     | 
| clientName    | Un string arbitrario con el nombre de la persona que recibirá: "Kevin Perez"      | 
| clientAddress    | Un string arbitrario con la dirección a donde se entrega. Ejemplo: <br> "Paseo de la Reforma 222. Interior 20"      | 


__Ejemplo de uso:__
 
**POST** [**https://controlpack.com/api/v1/orders**]()  
**Request body**
<pre>
{
    "delivery": {
    	"lat":  37.71283,
    	"long": -122.13901
    },
    "pickup": {
    	"id": 37.91283,
    	"asdf": -123.13901
    },
	"clientPhone": 1231202033,
   	"clientName": "Kevin Perez",
   	"clientAddress": "Paseo de la Reforma 222, int. 65"
}
</pre>

Se cotiza un envío del angel de la independencia a la fuente de la cibeles  

**Respuesta:**
<pre>
{
    "order": {
    	"id": 1022, //INT numero de preorden
		"possible": True, //BOOLEAN sobre si se puede completar en breve
		"cost": 25000, //INT de centavos mexicanos
		"eta": 19, //INT de minutos
    }
}
</pre>

## GET /orders/:id

Se solicita una orden en específico a través de su ID.
 

__Ejemplo de uso:__
 
**GET** [**https://controlpack.com/api/v1/orders/1022**]()  

Se checa el estado de la orden 1022
   
**Respuesta:**
<pre>
{
    "order": {
    	 //Status posibles: [cotizacion, confirmado, procesado, entregando, entregado]
        "status": cotizacion, //STRING con el estado
        "requested": False //Boolean que indica si ya se pidió 
        "id": 1022, //INT numero de orden
        "cost": 25000, //INT de centavos mexicanos
        "orderDate": 2017-04-17T02:00:00.000Z, //Date en que se pidió
        "pickupDate": 2017-04-17T02:10:00.000Z, //Date en que se recogió
        "deliveryDate": 2017-04-17T02:20:00.000Z, //Date en que se entregó
        "estimatedArrival": 2017-04-17T02:18:00.000Z //Date estimada entrega
        "currently": "19.4376401,-99.1758606", //String con las coordenadas live
        "clientPhone": 222123123, //INT with phone number
        "clientName": "Kevin Perez", //INT with phone number
        "clientAddress": "Paseo de la Reforma 222" //STRING con la dirección
    }
}
</pre>

## POST /orders/:id

Petición para actualizar una orden. Puede confirmarse el status o actualizar la información del cliente
 

__Ejemplo de uso:__
 
**POST** [**https://controlpack.com/api/v1/orders/1022**]()  

Se cotiza un envío del angel de la independencia a la fuente de la cibeles  

**Request body**
<pre>
{
	"status": "cotizacion", //STRING con el estado
	"request": True, //Boolean que solicita el pedido y activa la orden
	"clientPhone": 222123123, //INT with phone number
	"clientName": "Kevin Perez", //INT with phone number
	"clientAddress": "Paseo de la Reforma 222" //STRING con la dirección
}
</pre>

Se cotiza un envío del angel de la independencia a la fuente de la cibeles  

**Respuesta:**
<pre>
{
    "order": {
    	 //Status posibles: [cotizacion, confirmado, procesado, entregando, entregado]
        "status": cotizacion, //STRING con el estado
        "requested": False //Boolean que indica si ya se pidió 
        "id": 1022, //INT numero de orden
        "cost": 25000, //INT de centavos mexicanos
        "orderDate": 2017-04-17T02:00:00.000Z, //Date en que se pidió
        "pickupDate": 2017-04-17T02:10:00.000Z, //Date en que se recogió
        "deliveryDate": 2017-04-17T02:20:00.000Z, //Date en que se entregó
        "estimatedArrival": 2017-04-17T02:18:00.000Z //Date estimada entrega
        "currently": "19.4376401,-99.1758606", //String con las coordenadas live
        "clientPhone": 222123123, //INT with phone number
        "clientName": "Kevin Perez", //INT with phone number
        "clientAddress": "Paseo de la Reforma 222" //STRING con la dirección
    }
}
</pre>

## DELETE /orders/:id

Borrar una orden
 

__Ejemplo de uso:__
 
**DELETE** [**https://controlpack.com/api/v1/orders/1022**]()  

Se borra una orden y regresa la información

**Respuesta:**
<pre>
{
    "order": {
    	 //Status posibles: [cotizacion, confirmado, procesado, entregando, entregado]
        "status": cotizacion, //STRING con el estado
        "requested": False //Boolean que indica si ya se pidió 
        "id": 1022, //INT numero de orden
        "cost": 25000, //INT de centavos mexicanos
        "orderDate": 2017-04-17T02:00:00.000Z, //Date en que se pidió
        "pickupDate": 2017-04-17T02:10:00.000Z, //Date en que se recogió
        "deliveryDate": 2017-04-17T02:20:00.000Z, //Date en que se entregó
        "estimatedArrival": 2017-04-17T02:18:00.000Z //Date estimada entrega
        "currently": "19.4376401,-99.1758606", //String con las coordenadas live
        "clientPhone": 222123123, //INT with phone number
        "clientName": "Kevin Perez", //INT with phone number
        "clientAddress": "Paseo de la Reforma 222" //STRING con la dirección
    }
}
</pre>

