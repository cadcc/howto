<script src="https://d3js.org/d3.v3.min.js"></script>

# Tercer Piso Edificio Norte

<div id="mapa_old_dcc">

<style>

.piso {
     stroke: #cccccc;
     stroke-width: 1;
     fill: #cfebf7;
}

.objeto_sala text {
    text-anchor: middle;
	alignment-baseline: middle;
	font-weight: normal;
	font-family: Helvetica;
}

.objeto_sala:hover text {
    font-weight: bold;
}

.objeto_sala_black text {
    color: white;
}

.sala_de_estudio {
    stroke: #dddddd;
    stroke-width: 1;
    fill: #6fbced;
}

.objeto_sala:hover .sala_de_estudio {
    stroke: #dddddd;
    stroke-width: 0.5;
    fill: #66b1e2;
}

.convivencia {
	stroke: #dddddd;
    stroke-width: 1;
	fill: #8cc2e3;
}

.objeto_sala:hover .convivencia {
    stroke: #dddddd;
    stroke-width: 0.5;
    fill: #77adce;
}

.oficina {
    stroke: #dddddd;
    stroke-width: 1;
    fill: #2b73a0;
}

.objeto_sala:hover .oficina {
    stroke: #dddddd;
    stroke-width: 0.5;
    fill: #185982;
}

.otros {
    stroke: #dddddd;
    stroke-width: 1;
    fill: #50a1d3;
}

.objeto_sala:hover .otros {
    stroke: #dddddd;
    stroke-width: 0.5;
    fill: #408dbc;
}

</style>

<script src="mapa_edificio_norte_d3.js"><script>

</div>

Agradecimientos al Grupo de Agilidad de Madrid por la estructura de este mapa.

# Coming soon

Entre los lugares importantes que pensamos agregar están:

* Salita
* Eniac
* Toqui
* Oficina CaDCC
* Laboratorio Ramón Picarte
* Auditorio Lorenzo
* Otras salas (Grace, Ada, Flajolet, Colossus (magister), Anakena (doctora2) )
