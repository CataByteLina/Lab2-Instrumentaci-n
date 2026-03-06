
# LAB 2 – Instrumentación Biomédica  
## Sistema Vestible para Monitoreo de Estrés Basado en GSR  

**Universidad Militar Nueva Granada**  
Ingeniería Biomédica  


## 1. Introducción

La eminencia hipotenar
<img width="225" height="225" alt="image" src="https://github.com/user-attachments/assets/5383abdb-2b62-4c1b-8d49-b0c9fcd99ede" />

Contexto Teórico: La actividad electrodérmica o EDA (siglas de Electrodermal Activity) comprende a todos aquellos fenómenos eléctricos que ocurren a nivel de la piel, incluidas las alteraciones de su capacidad para conducir la electricidad, a la cual se le conoce como conductancia cutánea [1]. Esta propiedad puede aumentar en magnitud ante diversosestímulos que incluyen desde una respiración profunda hasta estímulos de naturaleza térmica o mecánica que son capaces de infligir dolor, tal y como lo han reportado varios estudios [2, 3]. A cada uno de los cambios del nivel basal de conductancia o SCL (Skin Conductance Level) se le denomina respuesta de conductancia cutánea o SCR (Skin Conductance Response).
Estas fluctuaciones suelen presentarse como un incremento súbito en la conductancia cutánea, la cual regresa a su valor inicial una vez transcurrido un tiempo notablemente mayor al que le tomó incrementar su valor [4], tal y como se muestra en la Figura 1.

La Actividad Electrodérmica (EDA) corresponde a las variaciones eléctricas de la piel asociadas a la actividad del sistema nervioso simpático. La medida más utilizada es la Respuesta Galvánica Cutánea (GSR), la cual refleja cambios en la conductancia cutánea debidos a la activación de las glándulas sudoríparas.

La GSR presenta dos componentes principales:

- SCL (Skin Conductance Level): Componente tónica ó estacionaria.
- SCR (Skin Conductance Response): Componente fásica ó transitoria.

Esta práctica consistió en diseñar un sistema vestible capaz de medir la GSR en tiempo real y estimar el nivel de estrés durante tareas cognitivas.


## 2. Objetivos

### 2.1 Objetivo General

Desarrollar un sistema vestible para la medición continua del nivel de estrés basado en GSR.

### 2.2 Objetivos Específicos

- Identificar las componentes tónica y fásica de la GSR.
- Diseñar un sistema seguro garantizando corrientes menores a 1 mA.
- Implementar transmisión alámbrica e inalámbrica.
- Evaluar cambios en GSR durante tareas cognitivas.
- Analizar aplicaciones y limitaciones del sistema desarrollado.


## 3. Marco Teórico

La actividad electrodérmica depende de la activación del sistema nervioso simpático, el cual regula la secreción de las glándulas sudoríparas ecrinas. Cuando aumenta la sudoración, disminuye la resistencia de la piel y aumenta la conductancia eléctrica.

Se distinguen:

Componente tónica (SCL):nivel basal de conductancia.
Componente fásica (SCR):respuestas transitorias ante estímulos.

La GSR no mide estrés directamente, sino activación autonómica.


## 4. Diseño del Sistema

### 4.1 Seguridad Eléctrica

De acuerdo con la norma IEC 60479, se deben limitar las corrientes que atraviesan el cuerpo humano.

La corriente se define como:
I = V / R


Caso extremo:


R_skin = 0 Ω


Con una alimentación de 5V:


R_min = 5V / 0.001A
R_min = 5000Ω


Se implementó una resistencia limitadora ≥ 5 kΩ en serie para garantizar que la corriente máxima no supere 1 mA.


### 4.2 Selección del Sitio Anatómico

Se eligió la eminencia hipotenar por:

- Alta densidad de glándulas sudoríparas.
- Estabilidad mecánica.
- Menor interferencia por movimiento.
- Facilidad de sujeción mediante banda elástica.


### 4.3 Componentes del Sistema

- Electrodos Ag/AgCl
- Resistencia limitadora ≥ 5 kΩ
- Amplificador operacional
- Microcontrolador ESP32
- Módulo Bluetooth
- Fuente DC 3.3–5 V


## 5. Parte B – Adquisición y Visualización
![WhatsApp Image 2026-03-05 at 11 28 15 AM](https://github.com/user-attachments/assets/0487ffaf-5d6b-48c1-b65a-3fa3f6164bf6)

### 5.1 Señal en Reposo

En reposo se observa:

- Nivel basal relativamente estable (SCL).
- Fluctuaciones espontáneas pequeñas.
- Ausencia de respuestas fásicas pronunciadas.

### 5.2 Inspiración Profunda

Durante una inspiración profunda se registró:

- Incremento súbito de conductancia (SCR).
- Retorno progresivo al valor basal.
- Activación simpática transitoria.

Valores registrados:

- Conductancia mínima: __________
- Conductancia máxima: __________

### 5.3 Clasificación de Estrés

| Nivel de Estrés | Rango de Conductancia |
|-----------------|-----------------------|
| Bajo            | __________            |
| Moderado        | __________            |
| Alto            | __________            |


## 6. Transmisión Inalámbrica

Se implementó comunicación Bluetooth mediante el ESP32 para:

- Enviar datos en tiempo real.
- Clasificar automáticamente el nivel de estrés.
- Mostrar mensajes en computador o dispositivo móvil.

El sistema genera alertas según los umbrales definidos.


## 7. Parte C – Evaluación Durante Tareas Cognitivas

Durante la resolución de problemas matemáticos:

- Aumentó la frecuencia de respuestas SCR.
- Se elevó el nivel basal (SCL).
- Se evidenció mayor activación simpática.

Esto confirma la relación entre carga cognitiva y variaciones en la GSR.


## 8. Análisis de Resultados

![WhatsApp Image 2026-03-04 at 9 44 20 PM](https://github.com/user-attachments/assets/ad64b5eb-3619-48b7-8937-982f73653f8b)


### 8.1 Monitoreo Ambulatorio

Aplicaciones:

- Oficinas (estrés laboral)
- Aulas universitarias
- Hogar

Limitaciones:

- Artefactos por movimiento.
- Variación por temperatura ambiental.
- Sudoración no asociada a estrés.
- Ruido eléctrico.

### 8.2 Aplicación en Neonatos

Posible utilidad en monitoreo autonómico temprano.

Limitaciones:

- Alta sensibilidad cutánea.
- Regulación térmica inmadura.
- Mayor variabilidad fisiológica.


## 9. Discusión

### 9.1 ¿Por qué la inspiración profunda incrementa la GSR?

La respiración profunda activa el sistema nervioso simpático, incrementando la actividad de las glándulas sudoríparas y aumentando la conductancia cutánea.

### 9.2 Ventajas y Desventajas de la GSR

Ventajas:

- No invasiva.
- Bajo costo.
- Fácil implementación.
- Alta sensibilidad simpática.

Desventajas:

- Baja especificidad fisiológica.
- Sensible a temperatura y movimiento.
- Variabilidad interindividual.


## 10. Conclusiones

Se diseñó un sistema vestible seguro y funcional capaz de medir variaciones en la respuesta galvánica cutánea asociadas a activación simpática.

Se comprobó que las tareas cognitivas incrementan la actividad fásica y pueden elevar el nivel basal de conductancia.

La GSR es una herramienta útil para monitoreo de activación autonómica, pero no debe considerarse un indicador exclusivo de estrés.

