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

<script>

var width = document.getElementById("mapa_old_dcc").offsetWidth
var height = width*430/706


var svg = d3.select("#mapa_old_dcc")
			.append("svg")
			.attr("width", width)
			.attr("height", height);

var group = svg.append('g')
				.attr("transform", "translate("+ width*1/20 + "," + height/43*5 + ") rotate(" + 0 + ")");

var line = d3.svg.line()
					.x(function(d) {return d.x})
					.y(function(d) {return d.y});

					
//Fondo del mapa
var datos_fondo = [
			{x: 0, y: 0},
			{x: width/10*9, y: 0},
			{x: width/10*9, y: height/43*33},
			{x: 0, y: height/43*33},
			{x: 0, y: 0}
			]
					
group.append("g").selectAll("path")
					.data([datos_fondo])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "piso");

					
//Laboratorio Lorenzo
var datos_lorenzo = [
			{x: 0, y: 0},
			{x: width/5, y: 0},
			{x: width/5, y: height*8/43},
			{x: 0, y: height*8/43},
			{x: 0, y: 0}
			];
					
var lorenzo = group.append("g")
				.attr("transform", "translate(" + 0 + "," + (height/430*165 - height*12/86)  + ")")
				.attr("class", "objeto_sala");
		
lorenzo.selectAll("path")
			.data([datos_lorenzo])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "sala_de_estudio");

if (width >= 650){
	lorenzo.append("text")
		.attr("transform", "translate(" + width/10 + "," + height*4/43  + ")")
		.text("Laboratorio Lorenzo");
}
		
//Sala Misteriosa de al lado de laboratorio lorenzo
var datos_lab_dichato = [
			{x: 0, y: 0},
			{x: width/5, y: 0},
			{x: width/5, y: height*4/43},
			{x: 0, y: height*4/43},
			{x: 0, y: 0}
			];
					
var lab_dichato = group.append("g")
								.attr("transform", "translate(" + 0 + "," + (height/430*245 - height*12/86)  + ")")
								.attr("class", "objeto_sala");
								
lab_dichato.selectAll("path")
						.data([datos_lab_dichato])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "otros");

if (width >= 650){
	lab_dichato.append("text")
			.attr("transform", "translate(" + width/10 + "," + height*5/86  + ")")
		.text("Laboratorio Dichato");
}
		
//Sala Fundadores
var datos_sala_fundadores = [
			{x: 0, y: 0},
			{x: width*125/1000, y: 0},
			{x: width*125/1000, y: height*6/43},
			{x: -width/80, y: height*6/43},
			{x: 0, y: 0}
			];
					
var sala_fundadores = group.append("g")
						.attr("transform", "translate(" + width*275/1000 + "," + (height/430*165 - height*12/86)  + ")")
						.attr("class", "objeto_sala");
		
sala_fundadores.selectAll("path")
			.data([datos_sala_fundadores])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){
	sala_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*2/43  + ")")
			.text("Sala");
				
	sala_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*4/43  + ")")
			.text("Fundadores");
}

//Sala misteriosa al lado de la fundadores
var datos_sala_al_lado_fundadores = [
			{x: -width/80, y: height*6/43},
			{x: width*125/1000, y: height*6/43},
			{x: width*125/1000, y: height*12/43},
			{x: width/80, y: height*12/43},
			{x: -width/80, y: height*6/43}
			];

var sala_al_lado_fundadores = group.append("g")
						.attr("transform", "translate(" + width*275/1000 + "," + (height/430*165 - height*12/86)  + ")")
						.attr("class", "objeto_sala");
		
sala_al_lado_fundadores.selectAll("path")
			.data([datos_sala_al_lado_fundadores])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){
	sala_al_lado_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*8/43  + ")")
			.text("Sala de");	

sala_al_lado_fundadores.append("text")
		.attr("transform", "translate(" + width*135/2000 + "," + height*10/43  + ")")
		.text("Reuniones 2");			
}		
		
//Banho 1		
var datos_banho_1_fondo = [
			{x: 0, y: 0},
			{x: width/20, y: 0},
			{x: width/20, y: height*12/43},
			{x: 0, y: height*12/43},
			{x: 0, y: 0}
			];

var datos_banho_1 = [
			{x: width/160, y: 0},
			{x: width/20 - width/160, y: 0},
			{x: width/20 - width/160, y: height*11/43},
			{x: width/160, y: height*11/43},
			{x: width/160, y: 0}
			];
			
var banho_1_fondo = group.append("g")
		.attr("transform", "translate(" + width*8/20 + "," + (height/430*165 - height*12/86)  + ")")
		.attr("class", "objeto_sala");
		
		
banho_1_fondo.selectAll("path")
		.data([datos_banho_1_fondo])
		.enter()
		.append("path")
		.attr("d", line)
		.attr("class", "otros");

var banho_1 = group.append("g")
		.attr("transform", "translate(" + width*8/20 + "," + (height/430*165 - height*12/86)  + ")")
		.attr("class", "objeto_sala");
		
		
banho_1.selectAll("path")
		.data([datos_banho_1])
		.enter()
		.append("path")
		.attr("d", line)
		.attr("class", "otros");

if (width >= 650){		
	banho_1.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*6/43  + ") rotate(90)")
			.text("Baño M");
}
		
//Entrada
var datos_entrada = [
			{x: 0, y: 0},
			{x: width*3/20, y: 0},
			{x: width*3/20, y: height*12/43},
			{x: 0, y: height*12/43},
			{x: 0, y: 0}
			];
					
var entrada = group.append("g")
		.attr("transform", "translate(" + width*9/20 + "," + (height/430*165 - height*12/86)  + ")")
		.attr("class", "objeto_sala");
		
entrada.selectAll("path")
			.data([datos_entrada])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){
	entrada.append("text")
			.attr("transform", "translate(" + width*3/40 + "," + height*6/43  + ")")
			.text("Entrada");
}
		
//Resto de la estructura del medio
var datos_resto = [
			{x: 0, y: 0},
			{x: width/10, y: 0},
			{x: width*3/40, y: +height*12/43},
			{x: 0, y: +height*12/43},
			{x: 0, y: 0}
			];
					
group.append("g")
		.attr("transform", "translate(" + width*6/10 + "," + (height/430*165 - height*12/86)  + ")")
		.selectAll("path")
			.data([datos_resto])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

			
//Cocina
var datos_cocina = [
			{x: 0, y: 0},
			{x: width*1/20, y: 0},
			{x: width*1/20, y: height*6/43},
			{x: 0, y: height*6/43},
			{x: 0, y: 0}
			];
					
var cocina = group.append("g")
		.attr("transform", "translate(" + width*625/1000 + "," + (height/430*165 - height*12/86)  + ")")
		.attr("class", "objeto_sala");

cocina.selectAll("path")
			.data([datos_cocina])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){			
	cocina.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*3/43  + ") rotate(90)")
			.text("Cocina");
}

//Banho_2		

var datos_banho_2 = [
			{x: width/160, y: 0},
			{x: width*1/20, y: 0},
			{x: width*1/20, y: height*22/172},
			{x: width/160, y: height*22/172},
			{x: width/160, y: 0}
			];
					
var cocina = group.append("g")
		.attr("transform", "translate(" + width*600/1000 + "," + (height/430*225 - height*12/86)  + ")")
		.attr("class", "objeto_sala");

cocina.selectAll("path")
			.data([datos_banho_2])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){			
	cocina.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*3/43  + ") rotate(90)")
			.text("Baño F");
}

//Auditorio Ramon Picarte
var datos_picarte = [
			{x: width/40, y: 0},
			{x: width*15/100, y: 0},
			{x: width*15/100, y: height*12/43},
			{x: 0, y: height*12/43},
			{x: width/40, y: 0}
			];
					
var picarte = group.append("g")
		.attr("transform", "translate(" + width*15/20 + "," + (height/430*225 - height*12/43)  + ")")
		.attr("class", "objeto_sala");

picarte.selectAll("path")
			.data([datos_picarte])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "otros");

if (width >= 650){
	picarte.append("text")
			.attr("transform", "translate(" + width*17/200 + "," + height*5/43  + ")")
			.text("Auditorio");
				
	picarte.append("text")
			.attr("transform", "translate(" + width*17/200 + "," + height*7/43  + ")")
			.text("Ramón Picarte");
}

//La Salita
var datos_salita = [
			{x: 0, y: 0},
			{x: width/100*15, y: 0},
			{x: width/100*15, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];
					
var salita = group.append("g")
		.attr("transform", "translate(" + 0 + "," + 0  + ")")
		.attr("class", "objeto_sala");
		
salita.selectAll("path")
			.data([datos_salita])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "convivencia");

if (width >= 650){
	salita.append("text")
			.attr("transform", "translate(" + width*15/200 + "," + height*75/860  + ")")
			.text("La Salita");
}

//La Ofisalita		
var datos_ofisalita = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];
					
var ofisalita = group.append("g")
					.attr("transform", "translate(" + width*15/100 + "," + 0  + ")")
					.attr("class", "objeto_sala");		
		
ofisalita.selectAll("path")
			.data([datos_ofisalita])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "convivencia");

if (width >= 650){
	ofisalita.append("text")
			.attr("transform", "translate(" + width*5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Ofisalita");
}			

//El resto de las salas
for(i = 4; i < 18; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];
					
	group.append("g")
			.attr("transform", "translate(" + width*5/100*i + "," + 0  + ")")
			.attr("class", "objeto_sala")
			.selectAll("path")
				.data([datos_ofisalita])
				.enter()
				.append("path")
				.attr("d", line)
				.attr("class", "oficina");
}


for(i = 2; i < 18; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];
					
	group.append("g")
			.attr("transform", "translate(" + width*5/100*i + "," + (height/430*255) + ")")
			.attr("class", "objeto_sala")
			.selectAll("path")
				.data([datos_ofisalita])
				.enter()
				.append("path")
				.attr("d", line)
				.attr("class", "oficina");
}


</script>

</div>

# Coming soon

Se agregarán 2 mapas más similares a los que están [aquí](https://salas-uchile.herokuapp.com/)

Entre los lugares importantes que pensamos agregar están:

* Eniac
* Toqui
* Grace
* Ada
* Flajolet 
* Colossus (magister)
* Anakena (doctora2) 

Disclaimer: Los mapas qe estan aquí están hechos al ojímetro, hay salas que son de distinto tamaño en la vida real :O

Agradecimientos al Grupo de Agilidad de Madrid por la estructura de los mapas.
