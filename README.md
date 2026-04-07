# Ortega-post1-u3

Laboratorio: Ensamblado y Ejecución Paso a Paso con DEBUG
 Descripción
  En este laboratorio se utilizó el depurador DEBUG en DOSBox para ensamblar programas directamente en memoria, ejecutar instrucciones paso a paso mediante el comando T y analizar el comportamiento de los registros y banderas del procesador. Se desarrollaron dos programas: uno de suma y otro con estructura de bucle utilizando la instrucción LOOP.
 Configuración del entorno
  MOUNT C C:\DOSWork
  C:
  MD LAB3POS2
  CD LAB3POS2
  DEBUG

 Checkpoint 1 — Programa de suma
  Código ensamblado
    A 100
    MOV AX,000A
    MOV BX,0005
    MOV CX,0003
    ADD AX,BX
    ADD AX,CX
    INT 20
  Tabla de traza
   Instrucción	AX	     BX	     CX	     IP	    ZF	CF	SF
   MOV AX,000A	000A	0000	0000	0103	NZ	NC	PL
   MOV BX,0005	000A	0005	0000	0106	NZ	NC	PL
   MOV CX,0003	000A	0005	0003	0109	NZ	NC	PL
   ADD AX,BX	000F	0005	0003	010B	NZ	NC	PL
   ADD AX,CX	0012	0005	0003	010D	NZ	NC	PL
   INT 20	    0012	0005	0003	01480	NZ	NC	PL
  Observaciones
   El valor final del registro AX es 0012 (18 en decimal), lo cual corresponde correctamente a la suma de los valores cargados. Las banderas indican que el resultado no es cero (NZ), no se produjo acarreo (NC) y el resultado es positivo (PL). El registro IP avanza de acuerdo con el tamaño de cada instrucción ejecutada.