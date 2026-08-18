# DigiRandom

Port del **Digimon World 3 Randomizer** de [markisha64][r], licencia MIT.

[r]: https://github.com/markisha64/dmw3-randomizer

## No es un parche

Su `patcher.json` está vacío a propósito: DigiRandom no cambia ningún fichero
del juego al instalarse. Lo que hace es **añadir una pestaña al lanzador**.

Desde ahí se elige la semilla y las opciones, y cada tirada **deja un mod
aparte** —`DigiRandom-<semilla>`— con el parche dentro. Se enciende y se apaga
como cualquier otro mod, se pueden tener varias tiradas guardadas, y pasarle la
semilla a otra persona le da exactamente la misma partida.

## Qué cambia respecto al programa de markisha64

El comportamiento, nada: mismas opciones y mismo algoritmo.

Lo único distinto es dónde se aplica. Su programa extrae la imagen del disco,
toca los ficheros y la vuelve a montar con mkpsxiso. Aquí el juego ya vive en
ficheros sueltos, así que esa mitad sobra.
