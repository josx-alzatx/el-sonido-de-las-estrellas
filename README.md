# el-sonido-de-las-estrellas

### Entrega del proyecto completo del final 

# Estrellas en vivo

Performance audiovisual en tiempo real. Una estrella hecha en **TouchDesigner** reacciona al ritmo de **Strudel**, la performer la controla desde **Open Stage Control** y el **público** vota su color desde el celular.

## Qué necesitas en el computador

- [TouchDesigner](https://derivative.ca/download)
- [Open Stage Control](https://openstagecontrol.ammd.net/download/)
- [Node.js](https://nodejs.org) (versión LTS), para el bridge del público
- [Visual Studio Code](https://code.visualstudio.com) con una cuenta de GitHub, para publicar la página del público
- Google Chrome, para Strudel

Todo corre en un solo computador.

## Puertos

| Puerto | Uso |
|---|---|
| 57120 | Strudel → TouchDesigner |
| 9002 | Interfaz de Open Stage Control |
| 9000 | Open Stage Control → TouchDesigner |
| 3000 | Página del público (bridge) |
| 7001 | Bridge del público → TouchDesigner |

## Cómo ponerlo en marcha

1. **TouchDesigner**: abre el archivo `.toe`. Ábrelo antes que lo demás.
2. **Strudel**: entra a [strudel.cc](https://strudel.cc) en Chrome, pega el código del `.txt` y pulsa **Ctrl + Enter**. Cuando el navegador pida permiso para acceder a otros dispositivos de la red, acéptalo.
3. **Open Stage Control**: en el lanzador carga el `.json`, con **port** `9002` y **send** `127.0.0.1:9000`, y pulsa **Start**.
4. **Bridge del público**: descomprime el `.zip`, ábrelo en VS Code y en la terminal ejecuta `npm install` (solo la primera vez) y después `npm start`. En la pestaña **PORTS** reenvía el puerto `3000` con visibilidad **Public**.
   - Panel de control: `http://localhost:3000/desktop/`
   - QR para proyectar: la URL de PORTS terminada en `/qr/`

El público escanea el QR y vota entre cuatro opciones. Cada ronda dura 45 segundos y el color que gana se aplica a la estrella.

## Consejos para el live performance

- En strudel con los $ o con los sliders, puedes ir haciendo live coding de la musica
- En Open stage puedes modificar algunos parametros de las estrellas (experimenta tu mismo para generar nuevas sensaciones)
- En el bridge la gente puede votar y se define, pero desde el desktop (solo lo tendrias tu) tambien puedes cambiar los colores sin necesidad de que haya una votación

### Espero que te guste y date la libertad creativa de generar tu propia performance :D

## pd: Aqui podran encontrar un link a youtube donde veran una demo de lo que puede lograrse con este sistema

## https://youtu.be/Y7j2kONKWdQ
