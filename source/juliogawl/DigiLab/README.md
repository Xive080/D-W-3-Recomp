# DigiLab

Las recompensas de cada enemigo: experiencia, experiencia de digievolución y
bits. La idea y la tabla de enemigos son de la herramienta de **JulioGawl**.

## No es un parche

Su `patcher.json` está vacío a propósito: DigiLab no cambia ningún fichero del
juego al arrancar. Lo que hace es **añadir una pestaña al lanzador**, y desde
ahí se escribe en `DMW3Game/PRO/STFGTREP.PRO`, que es un fichero de datos.

Por eso es un mod del apartado LANZADOR. Al instalarlo aparece su pestaña; al
quitarlo desaparece.

## Qué lleva

- `digilab.tsv` — los 333 enemigos con dónde está cada recompensa dentro del
  fichero de datos.
- `mod.ini` — la ficha.

Los cambios se hacen sobre los valores **originales**, no sobre los que haya
puestos, así que multiplicar dos veces no compone: siempre parte de lo que traía
el juego.
