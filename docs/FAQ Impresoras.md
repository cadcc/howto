# FAQ de Impresoras

---

## ¿Cómo se cuentas impresiones me quedan?

En un computador de anakena (como los del toqui) abre la terminal y escribe `papel`. Eso es todo, de verdad que es así de fácil... yo sigo sorprendido hasta el día de hoy.

---

## ¿Cómo imprimo a través de la terminal como hacker en el DCC?

Desde un computador del Toqui puedes escribir esto en la terminal
`pdf2ps filename.pdf out.ps`
Y luego esto para imprimir en el toqui:
`duplex -l out.ps|lpr`
o esto para imprimir en la impresora de la salita:
`duplex -l out.ps|lpr -P hp-335`
y magia.


Si estás desde tu computador tienes que primero copiar el archivo al servidor de anakena con scp:
`scp archivo.pdf usuario@anakena.dcc.uchile.cl:~/`
Y luego meterte a anakena con tu cuenta por ssh:
`ssh usuario@anakena.dcc.uchile.cl`
Y haces lo anterior como si estuvieras dentro de un computador en el Toqui (porque en teoría lo estas).

---
