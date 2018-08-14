# FAQ de Impresoras

---

## �C�mo se cuentas impresiones me quedan?

En un computador de anakena (como los del toqui) abre la terminal y escribe `papel`. Eso es todo, de verdad que es as� de f�cil... yo sigo sorprendido hasta el d�a de hoy. Tambi�n puedes revisar la cuota de papel de tus amigos escribiendo `papel <nombre_de_usuario>`.

---

## �C�mo imprimo a trav�s de la terminal como hacker en el DCC?

Desde un computador del Toqui puedes escribir esto en la terminal
`lpr filename.pdf`
Sin embargo, el archivo se imprime con la configuraci�n por defecto (una p�gina por hoja).

### Oye, �entonces c�mo imprimo a doble cara?

Puedes usar el comando `duplex`, pero solo funciona en archivos con formato Postscript, as� que primero debes escribir
`pdf2ps filename.pdf out.ps`
Y luego esto para imprimir en el toqui:
`duplex -l out.ps|lpr`
o esto para imprimir en la impresora de la salita:
`duplex -l out.ps|lpr -P hp-335`
y magia.

Disclaimer: El `-l` indica que el archivo se va a imprimir por el borde corto, si se omite se imprimir� por el borde largo.

Si est�s desde tu computador tienes que primero copiar el archivo al servidor de anakena con scp:
`scp archivo.pdf usuario@anakena.dcc.uchile.cl:~/`
Y luego meterte a anakena con tu cuenta por ssh:
`ssh usuario@anakena.dcc.uchile.cl`
Y haces lo anterior como si estuvieras dentro de un computador en el Toqui (porque en teor�a lo estas).

---
