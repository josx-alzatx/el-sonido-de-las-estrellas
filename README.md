# el-sonido-de-las-estrellas

# Estrellas en vivo

Performance audiovisual en tiempo real. Una estrella hecha en **TouchDesigner** reacciona al ritmo de **Strudel**, la performer la controla desde **Open Stage Control** y el **público** vota su color desde el celular.

## Sobre la obra

**Intención.** *Estrellas en vivo* explora la vida de una estrella como un proceso que no controla una sola persona. La performer construye el ritmo y la forma de la estrella en tiempo real, mientras el público decide en qué etapa de su vida se encuentra: si nace en una nebulosa, arde como gigante azul, envejece como gigante roja o explota como supernova. La obra busca que la imagen sea el resultado de una negociación entre quien actúa y quienes observan, y que el desorden de las figuras que aparecen con cada sonido haga sentir el espacio como algo vivo e inestable.

**Percepción.** El público percibe la obra por dos vías a la vez. Por la vista y el oído, porque cada golpe del ritmo hace pulsar la estrella y aparecer figuras, de modo que el sonido se "ve". Y por la participación, porque al votar desde el celular ven cómo su decisión, sumada a la de los demás, cambia el color de la estrella con un fundido lento. La espera de cada ronda genera expectativa, y el cambio de color se vuelve un momento compartido por toda la sala.

**Sistema técnico.** La imagen se genera en TouchDesigner. Strudel, desde el navegador, envía por OSC cada evento musical, que dispara pulsos en la estrella y la aparición de figuras. Open Stage Control funciona como la interfaz del performer, con faders y perillas que controlan la expansión, la rotación, las puntas y otros parámetros. Para el público hay un servidor propio en Node.js con socket.io: el público entra escaneando un QR, vota entre cuatro opciones y el servidor cuenta los votos (uno por celular y por ronda) y envía el color ganador a TouchDesigner por OSC/UDP.

## Reflexión después de la performance

Luego de hacer este testeo con un grupo de personas cercanas me dijeron que les gusto mucho el tema y la estetica y que la musica al ser de cierta manera "alocada" hace que la performance se sienta movida y no llegue a sentirse como aburrido o repetitivo, esto tambien es ayudado por el strudel debido a todos los items que puedes mover para cambiar escalas o sonidos.

## Guía para usarlo

### Qué necesitas en el computador

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
