---
layout: post
title: "Cómo hacer cine con IA gratis en 5 pasos"
date: 2025-06-03 05:47:00 -03:00
categories: [IA, Tecnología]
---

¿Siempre quisiste hacer videos y no sabías cómo hacerlos?

¿O tenés ganas de hacer tu propio anime o película de Hollywood?

Hoy todo es posible con la IA.

Nuestro aliado más fuerte de hoy es **Hugging Face**.

Hugging Face es una empresa de tecnología especializada en inteligencia artificial, conocida por su plataforma abierta para modelos de machine learning. Es como un "GitHub de la IA": ofrece una gran colección de modelos, demos y herramientas para experimentar sin tener que construir todo desde cero.

Hoy el trabajo es bastante manual, pero muchas opciones de la plataforma brindan la posibilidad de usar API. Este post va a centrarse en una ruta práctica y visual usando modelos accesibles.

En esta ocasión vamos a usar a [La Chica del Abrigo Azul](https://soymarcosba.blogspot.com/2023/08/la-chica-del-abrigo-azul.html), una imagen que me gustó y que funciona muy bien para transformar en un video.

En el caso que no tengamos el prompt, podemos generar una idea de cómo pudo haber sido generada.

## ¿Cómo saber cómo fue hecha una imagen?

Vamos a usar para esto [Florence-2](https://huggingface.co/spaces/SkalskiP/better-florence-2), un modelo que tiene la capacidad de hacer una descripción detallada de una imagen.

#### Configuración de Florence-2

Por lo general obtengo buenos resultados usando la siguiente configuración:

- **Model:** microsoft/Florence-2-large
- **Task:** More Detailed Caption

Nos va a dar una descripción bastante bien desarrollada.

```text
The image is a digital portrait of a young woman with long, wavy blue hair. She is wearing a blue jacket and has a serious expression on her face. The background is a dark blue with orange and pink tones.
```

Aunque se acerca bastante, le falta información clave para ciertos aspectos de la original, pero el resultado es bastante decente.

## Generación de imagen

Una vez que tenemos el prompt (original o de Florence-2), nos movemos a [Playground v2.5](https://huggingface.co/spaces/playgroundai/playground-v2.5).

**Playground v2.5** es un modelo bastante bueno, que genera resultados con muy buena calidad. Para obtener el resultado que se muestra en este artículo diría que conviene usar solo este modelo, para mantener una coherencia visual alta.

Acá generamos la imagen para luego pasar a darle vida.

Si usamos la descripción de Florence-2, nos genera algo como la imagen principal de este artículo.

_No hay mucha ciencia en este paso, más que elegir el tamaño de la imagen._

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgkxi85_Cq0wsfdfZoMAFi8wbh6ot87x18VxG8_o94Qh5vzihE5)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgkxi85_Cq0wsfdfZoMAFi8wbh6ot87x18VxG8_o94Qh5vzihE5)

Como se ve, la imagen no es mala, pero no es exactamente la misma.

Pero esta sería la original:

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-oW8MkOy6uLw-PeADjBTqQi3n1AAuyy8k0ZqGkgSbx-UHalm)

_Clara diferencia de estilos._

Para tener buenos resultados estas son las resoluciones que funcionan mejor:

**1:1 (cuadrado)**

- 512×512
- 768×768
- 1024×1024

**4:5 (vertical)**

- 512×640
- 768×960

**3:4 (vertical)**

- 576×768
- 768×1024

**2:3 (vertical)**

- 512×768
- 640×960

**9:16 (vertical)**

- 576×1024
- 864×1536

**16:9 (horizontal)**

- 1024×576
- 1536×864

**3:2 (horizontal)**

- 768×512
- 960×640

**4:3 (horizontal)**

- 768×576
- 1024×768

**21:9 (horizontal)**

- 1008×432
- 1344×576

El resto de las opciones para modificar por lo general las dejo como están, pero sos libre de experimentar resultados.

## Magia de Cine

Ahora solo nos queda hacer magia: lograr que esa imagen tenga vida, una corta, porque la opción que vamos a usar solo te deja hacer menos de 4 segundos, pero algo es algo.

Como si fuésemos un director de cine cual Spielberg, le tenemos que indicar al modelo de IA que queremos que sea el video.

Si no tenemos una idea clara de qué queremos, podemos recurrir a nuestro fiel amigo ChatGPT u otro modelo como Gemini, y pedir algo así:

```text
Convertí esta descripción de imagen en instrucciones detalladas para generar un video de 5 segundos. Incluí en un solo párrafo información sobre los movimientos de cámara y personaje, el estilo visual y la duración de cada plano.
```

Como resultado nos va a dar las indicaciones necesarias para generar el video.

Ahora que tenemos esto, nos dirigimos a usar el modelo de IA [Wan 2.1](https://huggingface.co/spaces/multimodalart/wan2-1-fast).

Y lo que hacemos es cargar la imagen que generamos y las instrucciones para hacer el video.

Elegimos el tiempo a gusto y esperamos a que se haga la magia.

> Nota: Hay otras opciones, repito que yo las dejo como están porque me dio buenos resultados, pero pueden probar a ver qué resultados les da. Como por ejemplo el Negative Prompt para asegurarse de no generar detalles raros.

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-oW8MkOy6uLw-PeADjBTqQi3n1AAuyy8k0ZqGkgSbx-UHalm)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-oW8MkOy6uLw-PeADjBTqQi3n1AAuyy8k0ZqGkgSbx-UHalm)

La clave está en combinar una imagen fuerte con una dirección clara del movimiento y la cinematografía. En pocas horas, una idea visual puede pasar de estática a animada sin necesidad de un estudio completo.
