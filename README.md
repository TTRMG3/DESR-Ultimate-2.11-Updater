[DESR_Ultimate_2.11_Updater_README.md](https://github.com/user-attachments/files/31874910/DESR_Ultimate_2.11_Updater_README.md)
# DESR-Ultimate-2.11-Updater
A solution for automatically upgrade your PSX DESR to firmware 2.11 without an update disc

## English

### What it is

**DESR Ultimate 2.11 Updater** is a free preservation tool for owners of
compatible Sony PSX DESR systems whose optical drive no longer works. It
prepares the official Sony 2.11 update payload from a USB drive and hands the
last, model-specific installation stage back to the console's own native
updater.

The included ELF is named **DESR UPDATE PREPARER**. It does not replace Sony's
updater, patch its payloads, or manually flash a collection of system files.
It reproduces the preparation job normally initiated by the official update
disc:

1. It copies the original update packages to the DESR's temporary update area.
2. It verifies the copied files.
3. It enables the native `Install` boot mode only after preparation succeeds.
4. On the next normal boot, the DESR itself backs up its current software,
   selects the appropriate packages for its own configuration, and performs
   the native installation.

The tool does not alter the supplied Sony update files. The final installation
and the choice of applicable packages remain the responsibility of Sony's code
running on the DESR.

### Why it exists

The official update method depends on an optical disc. A failed reader can make
an otherwise healthy DESR impossible to update. This project provides a simple
USB-based route to the same native update process, intended for preservation,
repair and continued use of these machines.

### Quick use

1. Make and verify a complete backup of the **same console**, including XFROM.
2. Copy the distribution contents to the root of a FAT32 USB drive.
3. Run `DESR_UPDATE_PREPARER.ELF` through uLaunchELF R3Z.
4. Follow the on-screen confirmation. Keep USB and power connected while it
   prepares and verifies the update files.
5. When it reports **INSTALL MODE ENABLED**, exit, power off normally, remove
   FMCB, then boot the DESR normally.
6. Do not interrupt the native Sony backup/update/install screens. The updater
   may remain at a percentage for some time while it verifies or finalises.

Use only with the supported PSX2 families covered by the original 2.11 update
package: DESR-5500, DESR-5700, DESR-7500 and DESR-7700. It is not for PSX1
models.

### Free distribution and Sony materials

This is a **free, non-commercial preservation project**. It is not sold, does
not offer a paid support service, and is not affiliated with or endorsed by
Sony. Sony update files included in a distribution remain Sony's property and
copyrighted material. They are kept unmodified and are provided solely so that
owners of compatible DESR hardware can restore the official update path when
the optical drive is unavailable.

Nothing in this project grants a licence to Sony software or makes any claim of
ownership over it. Laws and platform rules vary by country; distributors and
users are responsible for assessing their own legal position. If hosting or
distribution becomes a concern, the preparer can also be distributed without
the Sony payloads and used with a user-supplied original update image.

### Development story

The project began with Teo Tormo's theory that the update disc did not itself
perform the final installation: instead, it prepared files on the HDD, set a
boot flag, and allowed the DESR's internal Update Manager to take over.

Teo directed the research, supplied the machines and materials, defined the
requirements, and performed the real hardware testing. Jarvis (OpenAI Codex)
examined the observable update process and the supplied original materials,
used reverse engineering to reconstruct the preparation workflow, and created
an independent ELF that performs that workflow. The DESR then performs the
second half — its own backup, package selection and installation — with Sony's
native updater.

This distinction matters: DESR UPDATE PREPARER is a bridge into the official
installer, not a replacement firmware installer.

### Important warnings

- **Provided AS IS.** There is no technical support, post-sale support,
  maintenance commitment, replacement service or obligation to answer requests.
  The project is shared as a community preservation gift.
- Experimental preservation software: use at your own risk.
- Make a verified backup of the specific console before use.
- Do not use an unstable DESR as your first test unit.
- Never interrupt power during the native update process.
- No warranty is offered against data loss, a failed update or an unbootable
  console.
- Any community documentation is voluntary and is not technical support.

### Credits and dependencies

- Project direction, concept, hardware and validation:
  **[Teo Tormo](https://www.arcadeartisan.com)**.
- Analysis and implementation: **Jarvis (OpenAI Codex)**.
- Launcher, device access and DESR storage infrastructure:
  [wLaunchELF R3Z — R3Z3N / Saildot4K](https://github.com/saildot4k/wLaunchELF_R3Z),
  building on [wLaunchELF ISR — israpps](https://github.com/israpps/wLaunchELF_ISR)
  and their upstream contributors.
- PS2 homebrew SDK and libraries:
  [PS2DEV / ps2sdk](https://github.com/ps2dev/ps2sdk) and
  [gsKit](https://github.com/ps2dev/gsKit).
- Sony update executable, packages and firmware: copyright Sony. They are not
  created, owned or modified by this project.

---

## Español

### Qué es

**DESR Ultimate 2.11 Updater** es una herramienta gratuita de preservación para
propietarios de sistemas Sony PSX DESR compatibles cuyo lector óptico ya no
funciona. Prepara desde USB el contenido de la actualización oficial Sony 2.11
y entrega la fase final específica para cada máquina, al actualizador nativo
de la propia consola.

El ELF incluido se llama **DESR UPDATE PREPARER**. No sustituye al actualizador
de Sony, no modifica sus paquetes ni instala manualmente un conjunto de
archivos de sistema. Reproduce el trabajo previo que normalmente inicia el
disco oficial:

1. Copia los paquetes originales al área temporal de actualización de la DESR.
2. Verifica los archivos copiados.
3. Activa el modo nativo `Install` únicamente cuando la preparación termina.
4. En el siguiente arranque normal, la DESR hace por sí misma una copia de su
   software, elige los paquetes apropiados para su configuración e instala la
   actualización mediante su proceso nativo.

La herramienta no altera los archivos de actualización de Sony. La instalación
final y la selección de paquetes aplicables siguen siendo responsabilidad del
código de Sony que se ejecuta dentro de la DESR.

### Por qué existe

El método oficial de actualización depende de un disco óptico. Si el lector
falla, una DESR que por lo demás funciona puede quedarse sin posibilidad de
actualizarse. Este proyecto ofrece una vía USB sencilla hacia ese mismo proceso
nativo, pensada para preservación, reparación y uso continuado de estas máquinas.

### Uso rápido

1. Haz y verifica un backup completo de **esa misma consola**, incluido XFROM.
2. Copia el contenido de la distribución a la raíz de un pendrive FAT32.
3. Ejecuta `DESR_UPDATE_PREPARER.ELF` mediante uLaunchELF R3Z.
4. Sigue la confirmación en pantalla. Mantén USB y corriente conectados durante
   la preparación y verificación de los archivos.
5. Cuando indique **INSTALL MODE ENABLED**, sal, apaga normalmente, retira FMCB
   y arranca la DESR de forma normal.
6. No interrumpas las pantallas nativas de copia, actualización e instalación
   de Sony. El porcentaje puede permanecer un tiempo sin cambiar mientras
   verifica o finaliza operaciones internas.

Úsalo solo con las familias PSX2 incluidas en el paquete original 2.11:
DESR-5500, DESR-5700, DESR-7500 y DESR-7700. No es una herramienta para PSX1.

### Distribución gratuita y archivos de Sony

Este es un proyecto de preservación **gratuito y no comercial**. No se vende,
no ofrece soporte de pago y no está afiliado ni respaldado por Sony. Los archivos
de actualización de Sony que pueda incluir una distribución siguen siendo
propiedad y material protegido de Sony. Se mantienen sin modificar y se ofrecen
únicamente para que propietarios de hardware DESR compatible puedan recuperar
la vía oficial de actualización cuando no disponen de lector óptico.

Este proyecto no concede ninguna licencia sobre el software de Sony ni reclama
su propiedad. Las leyes y normas de cada plataforma cambian según el país; cada
distribuidor y usuario debe valorar su propia situación legal. Si el alojamiento
o la distribución plantean problemas, el preparador también puede distribuirse
sin los paquetes de Sony y utilizar una imagen original aportada por el usuario.

### Cómo se desarrolló

El proyecto partió de la teoría de Teo Tormo de que el disco de actualización
no realizaba por sí solo la instalación final: preparaba archivos en el HDD,
activaba un bootflag y dejaba que el Update Manager interno de la DESR tomara el
control.

Teo dirigió la investigación, aportó máquinas y material, definió los
requisitos y realizó las pruebas reales de hardware. Jarvis (OpenAI Codex)
examinó el proceso observable y el material original aportado, utilizó
ingeniería inversa para reconstruir el flujo de preparación y creó un ELF
independiente que lo reproduce. La DESR realiza después la segunda mitad —su
copia propia, selección de paquetes e instalación— con el actualizador nativo
de Sony.

Esta distinción es importante: DESR UPDATE PREPARER es un puente hacia el
instalador oficial, no un sustituto de firmware.

### Advertencias importantes

- **Se distribuye TAL CUAL / AS IS.** No existe soporte técnico, posventa,
  compromiso de mantenimiento, servicio de sustitución ni obligación de
  responder consultas. El proyecto se comparte como un regalo de preservación
  para la comunidad.
- Software experimental de preservación: úsalo bajo tu responsabilidad.
- Haz un backup verificado de la consola concreta antes de utilizarlo.
- No uses una DESR inestable como primera unidad de prueba.
- Nunca interrumpas la corriente durante el proceso nativo de actualización.
- No se ofrece garantía frente a pérdida de datos, actualización fallida o
  consola que no arranque.
- Cualquier documentación comunitaria es voluntaria y no constituye soporte
  técnico.

### Créditos y dependencias

- Dirección del proyecto, concepto, hardware y validación:
  **[Teo Tormo](https://www.arcadeartisan.com)**.
- Análisis e implementación: **Jarvis (OpenAI Codex)**.
- Lanzador, acceso a dispositivos e infraestructura de almacenamiento DESR:
  [wLaunchELF R3Z — R3Z3N / Saildot4K](https://github.com/saildot4k/wLaunchELF_R3Z),
  basado en [wLaunchELF ISR — israpps](https://github.com/israpps/wLaunchELF_ISR)
  y sus colaboradores anteriores.
- SDK y bibliotecas homebrew de PS2:
  [PS2DEV / ps2sdk](https://github.com/ps2dev/ps2sdk) y
  [gsKit](https://github.com/ps2dev/gsKit).
- El ejecutable, paquetes y firmware de actualización Sony son copyright de
  Sony. Este proyecto no los crea, posee ni modifica.
