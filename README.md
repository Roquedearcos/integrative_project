# Control de acceso en fábrica mediante visión por computador y PLN
Descripción general
Este proyecto simula un sistema de control de acceso en una fábrica mediante Visión por Computador y Procesamiento de Lenguaje Natural. Su objetivo es permitir o denegar el paso a trabajadores en función de si cumplen con la normativa de seguridad (EPIs).

El sistema consta de tres módulos principales:

## modulo_pln.py

Se encarga de extraer los Equipamientos de Protección Individual (EPIs) desde un PDF no estandarizado.

Utiliza la API de ChatGPT para procesar el texto y genera un archivo JSON con los EPIs requeridos.

## simulacion.py

Simula la cámara de una fábrica.

Permite introducir manualmente imágenes para probar el sistema sin necesidad de hardware.

## modulo_vc.py

Analiza las imágenes utilizando el modelo Qwen2-VL-7B-Instruct (ejecutado en el CESGA).

Determina si el trabajador cumple con los EPIs necesarios y decide si se le permite el acceso.

## ⚙️ Requisitos
Python 3.9+

openai (para la API de ChatGPT)

torch, transformers, opencv, etc. (detallar según el código real)

Acceso al CESGA (si se desea ejecutar el modelo completo)

