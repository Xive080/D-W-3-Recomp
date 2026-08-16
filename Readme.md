
Digimon World 3 Recomp



### 🛠️ Infraestructura de plataforma / Platform Infrastructure

| Sistema / System (ES) | System (EN) | Estado / Status | Dónde está / Location (ES) | Location & Details (EN) |
|---|---|:---:|---|---|
| **Arranque sin BIOS** | BIOS-less Boot | ✅ | Instantánea de arranque; quedan 1,8 KB de constantes en `Engine/datos_kernel.bin` | Boot snapshot; 1.8 KB of constants remaining in `Engine/datos_kernel.bin` |
| **Kernel de PS1 (servicios)** | PS1 Kernel (services) | ✅ 30/35 | `Src/KERNEL`, `runtime/hle_kernel_svc.c` — `KERNEL.md` | `Src/KERNEL`, `runtime/hle_kernel_svc.c` — `KERNEL.md` |
| **Sin imagen de disco** | No Disc Image | ✅ | 2.382 ficheros sueltos en `DMW3Game/` | 2,382 loose files in `DMW3Game/` |
| **Tarjeta de memoria** | Memory Card | ✅ sustituida | `runtime/hle_bu_device.c` — partidas en `.sav` nativos | `runtime/hle_bu_device.c` — save files in native `.sav` format |
| **Guardado** | Save System | ✅ cerrado | Sólo ficheros, modelo del port de FF VII de 1998 | Files only, based on the 1998 FF VII PC port save model |
| **Mando / teclado** | Controller / Keyboard | ✅ | `psx_controles.c`, `psx_keybinds.c` | `psx_controles.c`, `psx_keybinds.c` |
| **Dibujo (GPU)** | Rendering (GPU) | ✅ funciona | Del motor: OpenGL, D3D12, Vulkan y software | Engine side: OpenGL, D3D12, Vulkan, and software renderer |
| **Sonido (SPU)** | Audio (SPU) | ✅ funciona | Del motor — `SONIDO.md` documenta el lado del juego | Engine side — `SONIDO.md` documents game-side audio logic |
| **Vídeo (MDEC)** | Video (MDEC) | ✅ funciona | Del motor | Engine side |
| **Mods** | Mods / Add-ons | ✅ | `DMW3Game/MODS`, con foto, autor, enlace e interruptor — `MODS.md` | `DMW3Game/MODS`, with photo, author, link, and toggle switch — `MODS.md` |

<br>

### 🎮 Sistemas del juego / Game Systems

| Sistema / System (ES) | System (EN) | Estado / Status | Qué falta / Details (ES) | Missing / Details (EN) |
|---|---|:---:|---|---|
| **Bucle principal del juego** | Main Game Loop | ❌ | Lo lleva el motor fotograma a fotograma; el del juego no está reconstruido | Handled frame-by-frame by the engine; game logic loop is not reconstructed |
| **Inicialización** | Initialization | 🟡 | El arranque sí; la preparación del montón no | Boot process done; heap setup pending |
| **Gestión de memoria del juego** | Game Memory Management | ❌ | El reservador propio del juego sin tocar | Custom game allocator untouched |
| **Índice de disco** | Disc Index | ✅ reconstruido | `Src/DISC/disc_index.c` | `Src/DISC/disc_index.c` |
| **Estado del juego: banderas, reloj y aleatorios** | **Game State: Flags, Clock & RNG** | ✅ **8 de 8** | `Src/Config/game_state.c`. Cerrado el 12/8/2026 y **verificado en marcha**, pilotando hasta el campo | `Src/Config/game_state.c`. Closed on 08/12/2026 and **verified in runtime**, steering through to the overworld |
| **Caché de ficheros** | File Cache | 🟡 3 de 12 func. | Las otras nueve llaman de vuelta al juego — `file_cache.c` explica por qué se pararon | Remaining nine functions call back into game code — `file_cache.c` explains halt reason |
| **Cargador de overlays** | Overlay Loader | 🟡 localizado | Los dos huecos y sus cargadores medidos — `OVERLAYS.md` | Both slots and their respective loaders measured — `OVERLAYS.md` |
| **Carga de mapas / teselas** | Map / Tile Loading | 🟡 muy medido | 15 sospechosos descartados; **parado a propósito** — `TESELAS.md` | 15 candidates ruled out; **intentionally paused** — `TESELAS.md` |
| **Cámara del campo** | Overworld Camera | 🟡 medida | Sigue al jugador; parcheable en vivo — `CAMARA.md` | Follows the player; live-patchable — `CAMARA.md` |
| **Zonas y guiones** | Zones & Scripts | 🟡 | 294 guiones y su tabla localizados — `ZONAS-Y-GUIONES.md` | 294 scripts and lookup table localized — `ZONAS-Y-GUIONES.md` |
| **Estado del jugador (fichas de Digimon)** | Player State (Digimon Sheets) | 🟡 | Estructura descrita — `ESTADO-DEL-PLAYER.md`. Distinto del anterior: aquello es por dónde va la partida, esto son las ocho fichas | Structure mapped out — `ESTADO-DEL-PLAYER.md`. Distinct from game state: that tracks progress, this handles the eight sheets |
| **Entidades / NPC** | Entities / NPCs | ❌ | Sin auditar | Not audited |
| **Combate** | Battle System | 🟡 | Fórmulas medidas (`COMBATE-FORMULAS.md`); `Src/FIGHT` compila pero no reclama funciones | Formulas measured (`COMBATE-FORMULAS.md`); `Src/FIGHT` compiles without linking functions |
| **Evoluciones** | Evolutions / Digivolution | 🟡 | Tablas descifradas — `EVOLUCIONES.md` | Lookup tables decoded — `EVOLUCIONES.md` |
| **Entrenamiento** | Training System | 🟡 | `Src/TRAINING/training.c` sirve funciones originales | `Src/TRAINING/training.c` provides original functions |
| **Cartas** | Card Game | 🟡 | Formato descrito — `CARTAS.md` | Data format documented — `CARTAS.md` |
| **Tienda** | Shop System | ❌ | Sólo identificada | Identified only |
| **Menús del juego** | Game Menus | 🟡 | Título medido y enganchado; el de pausa se detecta de forma frágil | Title menu measured & hooked; pause menu detection is brittle |
| **Texto y diálogos** | Text & Dialogues | 🟡 | Formato y fuente descifrados — `TEXTO-DEL-JUEGO.md`, `IDIOMA.md` | Format and font decoded — `TEXTO-DEL-JUEGO.md`, `IDIOMA.md` |
| **Eventos del kernel** | Kernel Events | 🟡 riesgo vivo | La entrega anidada puede colgar el emulador sin dar error | Nested dispatch can freeze emulator silently |
| **Máquinas de estados** | State Machines | 🟡 | La del escenario descrita; las demás no | Stage state machine documented; others pending |
| **Tablas globales** | Global Tables | ✅ indexadas | `Src/Config/memory_map.h` — el índice de todo lo medido | `Src/Config/memory_map.h` — index of all measured elements |
| **Matemáticas / GTE** | Math / GTE | ❌ | Lo ejecuta el motor; no auditado como sistema | Executed by engine; not audited as a system |
| **Renderizado del juego** | Game Rendering | ❌ | Las tres pasadas del escenario descritas, el código no | Three stage rendering passes documented, code unreviewed |
| **Funciones compartidas** | Shared Functions | ❌ | Sin catalogar | Uncategorized |
