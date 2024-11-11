# Práctica 9

## Integrantes

- Dante Mejía Silva
- Atzin Morales Alejandre

## Introducción

En esta práctica de laboratorio, se utilizó un brazo robótico Epson para realizar una tarea de posicionamiento y ensamblaje de componentes. El objetivo consistió en mover dos cajitas a posiciones específicas y colocar en cada una dos fusibles de diferentes bases. Para ello, se programó una secuencia de movimientos utilizando puntos preestablecidos, controlando la potencia y velocidad del brazo.

Entre las funciones principales empleadas se encuentran:
- `Reset`: para reiniciar el sistema antes de iniciar los movimientos.
- `Motor On` y `Motor Off`: para activar y desactivar los motores en momentos específicos.
- `Power High` y `Power Low`: para ajustar la potencia en diferentes etapas del proceso.
- `Speed` y `Accel`: para establecer la velocidad y aceleración del brazo, optimizando los tiempos de desplazamiento.
- `Go`: para dirigir al robot a posiciones predefinidas, marcadas como puntos críticos (`CP`).
- `Home`: para retornar el brazo a la posición de inicio tras completar la tarea.

Este conjunto de funciones permitió realizar una secuencia eficiente y controlada para el ensamblaje de fusibles en las bases designadas.

## Instrucciones

En primer lugar se desarrolló el siguiente codigo que realizaba toda la secuencia planteada en un inicio.
```
Function main
	Reset
	Motor On
	Power High
	Speed 30
	Accel 30, 30
	SpeedS 200
	AccelS 2000, 2000
	
	Home
	On 2
	Go Caja_Izq_4 CP
	Go Caja_Izq_3 CP
	Go Caja_Izq_2 CP
	Go Caja_Izq_1
	
	Off 2
	
	Go Caja_Izq_1 CP
	Go Caja_Izq_2 CP
	Go Caja_Izq_3 CP
	
	
	Go Base1_4 CP
	Go Base1_3 CP
	Go Base1_2 CP
	Go Base1_1
	
	On 2
	
	Go Base1_1 CP
	Go Base1_2 CP
	Go Base1_3 CP
	
	Go Caja_Der_4 CP
	Go Caja_Der_3 CP
	Go Caja_Der_2 CP
	Go Caja_Der_1
	
	Off 2
	
	Go Caja_Der_1 CP
	Go Caja_Der_2 CP
	Go Caja_Der_3 CP
	
	Go Base3_4 CP
	Go Base3_3 CP
	Go Base3_2 CP
	Go Base3_1
	
	On 2
	
	Go Base3_1 CP
	Go Base3_2 CP
	Go Base3_3 CP
	
	Go Fusible1_izq_4 CP
	Go Fusible1_izq_3 CP
	Go Fusible1_izq_2 CP
	Go Fusible1_izq_1
	
	Off 2
	
	Go Fusible1_izq_1 CP
	Go Fusible1_izq_2 CP
	Go Fusible1_izq_3 CP
	
	Go Base1_Fus_Izq_4 CP
	Go Base1_Fus_Izq_3 CP
	Go Base1_Fus_Izq_2 CP
	Go Base1_Fus_Izq_1
	
	On 2
	
	Go Base1_Fus_Izq_1 CP
	Go Base1_Fus_Izq_2 CP
	Go Base1_Fus_Izq_3 CP
	
	Go Fusible2_izq_4 CP
	Go Fusible2_izq_3 CP
	Go Fusible2_izq_2 CP
	Go Fusible2_izq_1
	
	Off 2
	
	Go Fusible2_izq_1 CP
	Go Fusible2_izq_2 CP
	Go Fusible2_izq_3 CP
	
	Go Base1_Fus_Der_4 CP
	Go Base1_Fus_Der_3 CP
	Go Base1_Fus_Der_2 CP
	Go Base1_Fus_Der_1
	
	On 2
	
	Go Base1_Fus_Der_1 CP
	Go Base1_Fus_Der_2 CP
	Go Base1_Fus_Der_3 CP
	
	
	
	Go Fusible3_izq_4 CP
	Go Fusible3_izq_3 CP
	Go Fusible3_izq_2 CP
	Go Fusible3_izq_1
	
	Off 2
	
	Go Fusible3_izq_1 CP
	Go Fusible3_izq_2 CP
	Go Fusible3_izq_3 CP
	
	Go Base3_Fus_Izq_4 CP
	Go Base3_Fus_Izq_3 CP
	Go Base3_Fus_Izq_2 CP
	Go Base3_Fus_Izq_1
	
	On 2
	
	Go Base3_Fus_Izq_1 CP
	Go Base3_Fus_Izq_2 CP
	Go Base3_Fus_Izq_3 CP
	
	Go Fusible1_Der_4 CP
	Go Fusible1_Der_3 CP
	Go Fusible1_Der_2 CP
	Go Fusible1_Der_1
	
	Off 2
	
	Go Fusible1_Der_1 CP
	Go Fusible1_Der_2 CP
	Go Fusible1_Der_3 CP
	
	Go Base3_Fus_Der_4 CP
	Go Base3_Fus_Der_3 CP
	Go Base3_Fus_Der_2 CP
	Go Base3_Fus_Der_1
	
	On 2
 Home
Power Low
Fend
```

Antes de probarlo de manera física se realizó una prueba simulada para garantizar el correcto trazado de la secuencia.

![image](https://github.com/user-attachments/assets/b97d4c83-d13f-4fbd-897d-b20857d3ba3e)

1. **Configuración inicial**:
   - `Reset`: Restablece el robot a su estado inicial.
   - `Motor On`: Activa los motores del robot.
   - `Power High`, `Speed`, `Accel`, `SpeedS` y `AccelS`: Configuran la potencia, velocidad y aceleración tanto en desplazamientos regulares como rápidos.

2. **Inicio de la secuencia de movimientos**:
   - `Home`: Lleva al robot a su posición de inicio.
   - `On 2` y `Off 2`: Activa o desactiva una pinza o actuador para recoger y soltar componentes, respectivamente.

3. **Movimientos hacia las cajas y bases**:
   - `Go` seguido de nombres como `Caja_Izq`, `Caja_Der`, `Base1`, `Base3`, `Fusible1`, `Fusible2`, etc.: Envía al robot a posiciones predefinidas para recoger o colocar componentes. 
   - Cada posición se indica con un sufijo (`_1`, `_2`, `_3`, `_4`) para especificar puntos exactos dentro de las cajas o bases.
   - `CP`: El sufijo `CP` en cada comando `Go` significa "Current Position" y le indica al robot que debe moverse hacia la siguiente posición manteniendo su orientación y referencia actuales. Esto permite que el robot siga una trayectoria precisa y constante, crucial en tareas de ensamblaje donde debe llegar a cada posición sin ajustar su orientación, asegurando la precisión al manipular los fusibles y las bases.

4. **Secuencia de ensamblaje**:
   - La secuencia de movimientos sigue un patrón de recoger fusibles de una posición y colocarlos en bases asignadas. Cada operación se completa con movimientos entre los puntos predefinidos y activaciones de la pinza.

5. **Retorno y apagado**:
   - `Home`: Lleva al robot de vuelta a la posición de inicio tras finalizar la tarea.
   - `Power Low`: Reduce la potencia al mínimo al concluir el proceso.
   - `Fend`: Marca el final de la función principal.
     
El resultado final de la secuencia se visualiza en la siguiente imagen:

![Imagen de WhatsApp 2024-11-04 a las 23 53 49_26747a37](https://github.com/user-attachments/assets/1a781fcc-fcc9-46b7-979d-a975d71875df)

## Conclusiones

***Atzin Morales Alejandre:*** Esta práctica de laboratorio con el brazo robótico Epson evidenció la importancia de una programación precisa y del control ajustado en cada etapa del proceso de ensamblaje. La implementación de funciones clave como “Motor On”, “Power High/Low” y “Speed/Accel” permitió ajustar la potencia, velocidad y aceleración en los movimientos, optimizando así la secuencia de posicionamiento y manipulación de los fusibles en sus respectivas bases. El propósito de la práctica fue colocar fusibles en posiciones específicas dentro de cajas en bases utilizando una secuencia precisa de movimientos, mediante puntos ya establecidos. Esto permitió aplicar conocimientos sobre funciones de control del robot como ajuste de potencia, velocidad y posiciones preestablecidas, optimizando la manipulación de piezas y mejorando la comprensión de la automatización en entornos industriales.

Por otra parte, el uso de funciones como “Go” con puntos críticos predefinidos (CP) facilitó un movimiento constante y preciso hacia las posiciones específicas de las cajas y bases, mientras que “On 2” y “Off 2” controlaron el agarre de los fusibles, asegurando una colocación exacta en cada base. La simulación previa fue esencial, ya que permitió anticipar y corregir posibles inconsistencias en la trayectoria, reforzando la precisión en cada fase y demostrando el potencial del brazo robótico para satisfacer los requisitos de una línea de ensamblaje industrial.



***Dante Mejía Silva:*** 

En conclusión, esta práctica de laboratorio permitió aplicar y comprender cómo un brazo robótico Epson puede ser programado para realizar tareas de manipulación y ensamblaje de componentes de manera automatizada. A través de una secuencia de movimientos controlados, el robot fue capaz de mover fusibles entre diferentes posiciones y colocarlos en bases específicas, todo ello con una alta precisión gracias al uso de puntos predefinidos y la función `CP` para mantener la orientación y trayectoria correcta en todo momento.

El uso de comandos como `Go` para alcanzar posiciones clave, junto con la activación de actuadores para recoger y soltar componentes, demostró la capacidad del robot para ejecutar tareas repetitivas con eficiencia y exactitud. Además, la configuración de parámetros como velocidad, aceleración y potencia, y el control de la secuencia mediante las funciones de inicio y apagado, permitió un manejo eficiente del robot durante toda la operación.

Esta experiencia subraya la importancia de la programación precisa y la integración de distintos comandos para lograr una automatización exitosa en tareas industriales, lo que demuestra el potencial de la robótica en aplicaciones de ensamblaje y manipulación de componentes.

## Referencias Bibliográficas 

[1] 	EpsonCompany, «Especialistas en automatización industrial». 2024, https://www.epson.es/es_ES/robots

