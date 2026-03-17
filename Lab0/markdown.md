# Entrega Lab 0
Agustin Ezequiel Heredia Urbinatti
44295961
agustin.heredia.urbinatti@mi.unc.edu.ar
https://github.com/AgU131/redes2026

# Preguntas conceptuales

## 1. ¿Cómo sabe el cliente que terminó de recibir la respuesta?

Porque en HTTP/1.0 el servidor cierra la conexión cuando termina de enviar la respuesta. Cuando el cliente hace `recv()` y recibe 0 bytes, lo toma como que ya no hay mas datos y asi termina.

## 2. ¿Qué parte del comportamiento depende de TCP y cuál de HTTP?

TCP se encarga del transporte confiable de los datos (conexión, orden, retransmisiones). HTTP define el formato de los mensajes que se envian sobre esa conexinn (request, headers, status line y body).

## 3. ¿Qué pasaría si el servidor no cerrara la conexión después de enviar la respuesta?

El cliente no sabria cuándo termina la respuesta y seguiria esperando mas datos. El programa podria quedar bloqueado esperando que lleguen datos que en realidad nunca van a llegar.

## 4. ¿Por qué la IP obtenida para el mismo hostname podría ser distinta entre ejecuciones (o entre máquinas)?

Porque muchos servicios usan varias IPs para el mismo dominio. El DNS puede devolver distintas direcciones para balancear carga o enviar al cliente al servidor más cercano.

## 5. ¿Por qué DNS suele usar UDP y HTTP usa TCP? ¿Qué pasaría si usáramos TCP para las consultas DNS en este cliente? (opcional, profundización)

DNS usa UDP porque las consultas son pequeñas y rapidas, y asi se evita el costo de establecer una conexión. HTTP usa TCP porque necesita una transmision confiable y ordenada de datos, especialmente cuando las respuestas pueden ser grandes, a diferencia de UDP que puede perder info en el camino.
Si usaramos TCP para las consultas DNS en este cliente habria mucho gasto de recursos y tiempo, seria ineficiente. Aunque es posible, o sea, seguiria andando pq DNS también puede usar TCP.
