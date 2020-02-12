---
layout: post
title: "Estrenamos ranking"
date: 2014-03-06 19:44:04 +0100
comments: true
sharing: true
footer: true
categories: [general, tute, ranking, android]
---
Acabo de publicar la primera actualización del [Tute a Cuatro](/juegos) en Google Play. Se trata de una nueva funcionalidad, un servicio de ranking entre los jugadores del Tute a Cuatro. Para ello, he creado un algoritmo de puntuación muy sencillo:

* En caso de victoria se consigue un número de puntos igual al número de juegos de la partida multiplicado por el factor de dificultad (1 para el nivel *Principiante*, 2 para el *Amateur*, 3 para el *Avanzado* y 4 para el *Profesional*).
* En caso de derrota se resta el doble de puntos del número de juegos de la partida.

Por ejemplo, en una partida a 6 juegos en el nivel *Avanzado* se conseguirían 18 puntos en caso de victoria y se restarían 12 en caso de derrota.

Con los puntos se obtiene el ranking para cada jugador y además el juego ofrece unas estadísticas básicas del número de juegos ganados, perdidos y el ratio. En la imagen adjunta podéis ver qué pinta tiene el ranking.

![Ranking](/images/ranking.png)

En cuanto a los cambios necesarios, la funcionalidad en sí es muy sencilla, pero ha necesitado cierto trabajo. Para los más curiosos os explico a grandes rasgos la arquitectura del sistema. 

La aplicación de tute almacena localmente las victorias/derrotas y el número de puntos. Tras el fin de una partida, se envía esta información al servidor de tute. El servidor se encarga de devolver el ranking cuando una aplicación de tute lo solicita. 

El servidor está alojado en [Openshift](https://www.openshift.com/), la nube de Red Hat. Estoy utilizando un [MySQL](http://www.mysql.com/) para la persistencia, mientras que la aplicación está desarrollada con [Restlet](http://restlet.org/) y desplegada en un contenedor de servlets [Tomcat](http://tomcat.apache.org/). Además, utilizo autenticación HTTP y JSON como formato de intercambio.

Como veis, ha llevado cierto trabajo. Espero que haya merecido la pena y que disfrutéis mucho del ranking. **¿Conseguirás ser el primero?** 

