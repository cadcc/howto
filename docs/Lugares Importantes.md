<script src="https://d3js.org/d3.v3.min.js"></script>

<style>

#legend {
	display: flex;
	flex-wrap: wrap;
}

#legend li {
	list-style-type: none;
	display: flex;
	align-items: center;
	width: 50%;
	margin-left: 0;
	margin-bottom: 0.3em;
	line-height: 1.1;
}

#legend li span {
	font-size: 2em;
	margin-top: -0.1em;
	margin-right: 0.2em;
}

.piso {
	 stroke: #1f1954;
	 stroke-width: 2;
	 fill: #e4e4f2;
}

.objeto_sala path {
	stroke: #1f1954;
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

.convivencia {
	color: #6693d6;
	fill: currentColor;
}

.objeto_sala:hover .convivencia {
	fill: #a6afb5;
}

.sala_de_estudio {
	color: #31c4b0;
	fill: currentColor;
}

.objeto_sala:hover .sala_de_estudio {
	fill: #a6afb5;
}

.auditorio {
	color: #f8df7c;
	fill: currentColor;
}

.objeto_sala:hover .auditorio {
	fill: #a6afb5;
}

.oficina_admin {
	color: #c2d1c7;
	fill: currentColor;
}

.objeto_sala:hover .oficina_admin {
	fill: #a6afb5;
}

.oficina_profe {
	color: #a6b7d9;
	fill: currentColor;
}

.objeto_sala:hover .oficina_profe {
	fill: #a6afb5;
}

.oficina_importante {
	color: #ff708a;
	fill: currentColor;
}

.objeto_sala:hover .oficina_importante {
	fill: #a6afb5;
}

.posgrado {
	color: #e7c7eb;
	fill: currentColor;
}

.objeto_sala:hover .posgrado {
	fill: #a6afb5;
}

.otros {
	color: #d0d3dd;
	fill: currentColor;
}

.objeto_sala:hover .otros {
	fill: #a6afb5;
}

svg text {
	font-size: 0.8em;
}

</style>

<ul id="legend">
	<li><span class="convivencia">●</span> Espacios comunitarios</li>
	<li><span class="sala_de_estudio">●</span> Zonas de estudio</li>
	<li><span class="oficina_profe">●</span> Oficinas profesores</li>
	<li><span class="oficina_admin">●</span> Oficinas administrativas</li>
	<li><span class="oficina_importante">●</span> Oficinas importantes para estudiantes</li>
	<li><span class="auditorio">●</span> Auditorios / Salas de reunión</li>
	<li><span class="posgrado">●</span> Posgrado</li>
	<li><span class="otros">●</span> Servicios y otros</li>
</ul>

# Tercer Piso Edificio Norte

<div id="mapa_old_dcc">

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

	lorenzo.append("text")
		.attr("transform", "translate(" + width/10 + "," + height*4/43  + ")")
		.text("Laboratorio Lorenzo");

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
						.attr("class", "posgrado");

	lab_dichato.append("text")
			.attr("transform", "translate(" + width/10 + "," + height*5/86  + ")")
		.text("Laboratorio Dichato");

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
			.attr("class", "auditorio");

	sala_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*2/43  + ")")
			.text("Sala");

	sala_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*4/43  + ")")
			.text("Fundadores");

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
			.attr("class", "auditorio");

	sala_al_lado_fundadores.append("text")
			.attr("transform", "translate(" + width*135/2000 + "," + height*8/43  + ")")
			.text("Sala de");   

sala_al_lado_fundadores.append("text")
		.attr("transform", "translate(" + width*135/2000 + "," + height*10/43  + ")")
		.text("Reuniones");              

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
 
	banho_1.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*6/43  + ") rotate(90)")
			.text("Baño ♂");

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

	entrada.append("text")
			.attr("transform", "translate(" + width*3/40 + "," + height*6/43  + ")")
			.text("Entrada");

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
	   
	cocina.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*3/43  + ") rotate(90)")
			.text("Cocina");

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
		 
	cocina.append("text")
			.attr("transform", "translate(" + width/40 + "," + height*3/43  + ") rotate(90)")
			.text("Baño ♀");

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
			.attr("class", "auditorio");

	picarte.append("text")
			.attr("transform", "translate(" + width*17/200 + "," + height*5/43  + ")")
			.text("Auditorio");

	picarte.append("text")
			.attr("transform", "translate(" + width*17/200 + "," + height*7/43  + ")")
			.text("Ramón Picarte");

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

	salita.append("text")
			.attr("transform", "translate(" + width*15/200 + "," + height*75/860  + ")")
			.text("La Salita");

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

	ofisalita.append("text")
			.attr("transform", "translate(" + width*5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Ofisalita");           

//Dirección
var datos_direccion = [
			{x: 0, y: 0},
			{x: width/100*5*2.5, y: 0},
			{x: width/100*5*2.5, y: height/430*104},
			{x: 0, y: height/430*104},
			{x: 0, y: 0}
			];

var direccion_departamento = group.append("g")
					.attr("transform", "translate(" + width*5*15.5/100 + "," + 0  + ")")
					.attr("class", "objeto_sala");

direccion_departamento.selectAll("path")
			.data([datos_direccion])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "oficina_admin");

	direccion_departamento.append("text")
			.attr("transform", "translate(" + width*12.5/200 + "," + height*100/860  + ")")
			.text("Dirección");

//El resto de las salas
for(i = 4; i < 9; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];

	var sala_misteriosa = group.append("g")
							.attr("transform", "translate(" + width*5/100*i + "," + 0  + ")")
							.attr("class", "objeto_sala");

	sala_misteriosa.selectAll("path")
						.data([datos_misteriosos])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "oficina_admin");

		sala_misteriosa.append("text")
			.attr("transform", "translate(" + width*5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Oficina " + (331 - (i - 4)) );           
}

//Secretarias PEC
var datos_sec_pec = [
			{x: 0, y: 0},
			{x: width/100*10, y: 0},
			{x: width/100*10, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];

	var sala_sec_pec = group.append("g")
			.attr("transform", "translate(" + width*5/100*(9) + "," + 0  + ")")
			.attr("class", "objeto_sala");

	sala_sec_pec.selectAll("path")
				.data([datos_sec_pec])
				.enter()
				.append("path")
				.attr("d", line)
				.attr("class", "oficina_admin");

		sala_sec_pec.append("text")
			.attr("transform", "translate(" + width*10/200 + "," + height*60/860  + ")")
			.text("Oficina");

		sala_sec_pec.append("text")
			.attr("transform", "translate(" + width*10/200 + "," + height*90/860  + ")")
			.text(326);


//Jefe PEC
var datos_jefe_pec = [
			{x: 0, y: 0},
			{x: width/100*7.5, y: 0},
			{x: width/100*7.5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];

	var sala_jefe_pec = group.append("g")
			.attr("transform", "translate(" + width*5/100*(11) + "," + 0  + ")")
			.attr("class", "objeto_sala");

	sala_jefe_pec.selectAll("path")
				.data([datos_jefe_pec])
				.enter()
				.append("path")
				.attr("d", line)
				.attr("class", "oficina_admin");

		sala_jefe_pec.append("text")
			.attr("transform", "translate(" + width*7.5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Oficina " + (325) );

//El resto de las salas
for(i = 11; i < 14; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];

	var sala_misteriosa = group.append("g")
							.attr("transform", "translate(" + width*5/100*(i + 1.5) + "," + 0  + ")")
							.attr("class", "objeto_sala");

	sala_misteriosa.selectAll("path")
						.data([datos_misteriosos])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "oficina_admin");

		sala_misteriosa.append("text")
			.attr("transform", "translate(" + width*5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Oficina " + (331 - (i - 4)) );
}


for(i = 2; i < 18; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: width/100*5, y: 0},
			{x: width/100*5, y: height/430*75},
			{x: 0, y: height/430*75},
			{x: 0, y: 0}
			];

	var sala_misteriosa = group.append("g")
							.attr("transform", "translate(" + width*5/100*i + "," + height/430*255  + ")")
							.attr("class", "objeto_sala");

	sala_misteriosa.selectAll("path")
						.data([datos_misteriosos])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "oficina_profe");

		sala_misteriosa.append("text")
			.attr("transform", "translate(" + width*5/200 + "," + height*75/860  + ") rotate(90)")
			.text("Oficina " + (301 + i) );
}



</script>
</div>



# Segundo Piso Edificio Poniente

<div id="mapa_2do_piso_poniente">

<script>
var width = document.getElementById("mapa_2do_piso_poniente").offsetWidth
var height = width*430/706


var svg = d3.select("#mapa_2do_piso_poniente")
			.append("svg")
			.attr("width", width)
			.attr("height", height);

var group = svg.append('g')
				.attr("transform", "translate("+ width*1/20 + "," + height/43*5 + ") rotate(" + 0 + ")");

var new_height = height/43*33
var new_width = width/10*9

//Fondo del mapa
var datos_fondo = [
			{x: 0, y: 0},
			{x: new_width, y: new_height*50/302},
			{x: new_width, y: new_height},
			{x: 0, y: new_height},
			{x: 0, y: 0}
			]

group.append("g").selectAll("path")
					.data([datos_fondo])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "piso");

//Lab Toqui
var datos_lab_toqui = [
			{x: 0, y: 0},
			{x: new_width/910*200, y: new_height/302*11},
			{x: new_width/910*200, y: new_height/302*113},
			{x: 0, y: new_height/302*113},
			{x: 0, y: 0}
			];

var lab_toqui = group.append("g")
						.attr("transform", "translate(" + (new_width/910*250) + "," + (new_height/302*14)  + ")")
						.attr("class", "objeto_sala");


lab_toqui.selectAll("path")
			.data([datos_lab_toqui])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "sala_de_estudio");


	lab_toqui.append("text")
			.attr("transform", "translate(" + new_width/910*100 + "," + (new_height/302*56 - height/43)  + ")")
			.text("Laboratorio");

	lab_toqui.append("text")
			.attr("transform", "translate(" + new_width/910*100 + "," + (new_height/302*56 + height/43)  + ")")
			.text("Toqui");

//Escalera
var escalera = group.append("g")
						.attr("transform", "translate(" + (new_width/910*505) + "," + (new_height/302*100)  + ")")
						.attr("class", "objeto_sala");

escalera.selectAll("circle")
			.data([[]])
			.enter()
			.append("circle")
			.attr("class", "otros")
			.style("stroke", "#1f1954")
			.attr("r", new_width/910*50)
			.attr("cx", 0)
			.attr("cy", 0);
			
escalera.append("text")
			.text("Escalera");

//Impresora
var datos_impresora = [
		{x: 0, y: 0},
		{x: new_width/910*50, y: 0},
		{x: new_width/910*50, y: new_height/302*50},
		{x: 0, y: new_height/302*50},
		{x: 0, y: 0}
		];

var impresora = group.append("g")
						.attr("transform", "translate(" + new_width/910*12*50 + "," + new_height/302*77  + ")")
						.attr("class", "objeto_sala");

impresora.selectAll("path")
					.data([datos_impresora])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "otros");

	impresora.append("text")
		.attr("transform", "translate(" + new_width/910*25 + "," + new_height/302*25 + ")")
		.text("Printer");

//Pieza Aseo
var datos_pieza_aseo = [
		{x: 0, y: 0},
		{x: new_width/910*50, y: new_height/302*11/4},
		{x: new_width/910*50, y: new_height/302*183/2},
		{x: 0, y: new_height/302*183/2},
		{x: 0, y: 0}
		];

var pieza_aseo = group.append("g")
						.attr("transform", "translate(" + new_width/910*650 + "," + new_height/604*72  + ")")
						.attr("class", "objeto_sala");

pieza_aseo.selectAll("path")
					.data([datos_pieza_aseo])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "oficina_admin");
   
	pieza_aseo.append("text")
		.attr("transform", "translate(" + (new_width/910*25) + "," + (new_height/302*178/4) + ") rotate(90)")
		.text("Auxiliares Aseo");

//Jefa de Estudios
var datos_jefa_estudios = [
		{x: 0, y: 0},
		{x: new_width/910*50, y: new_height/302*11/4},
		{x: new_width/910*50, y: new_height/302*89},
		{x: 0, y: new_height/302*89},
		{x: 0, y: 0}
		];

var jefa_estudios = group.append("g")
						.attr("transform", "translate(" + new_width/910*700 + "," + new_height/604*(72 + 11/2)  + ")")
						.attr("class", "objeto_sala");

jefa_estudios.selectAll("path")
					.data([datos_jefa_estudios])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "oficina_importante");

	jefa_estudios.append("text")
		.attr("transform", "translate(" + (new_width/910*25 + new_width/910*10) + "," + (new_height/302*178/4) + ") rotate(90)")
		.text("Jefa");

	jefa_estudios.append("text")
		.attr("transform", "translate(" + (new_width/910*25 - new_width/910*10) + "," + (new_height/302*178/4) + ") rotate(90)")
		.text("Estudios");

//Secretaría Docente
var datos_secretaria_docente = [
		{x: 0, y: 0},
		{x: new_width/910*100, y: new_height/302*11/2},
		{x: new_width/910*100, y: new_height/302*66},
		{x: 0, y: new_height/302*66},
		{x: 0, y: 0}
		];

var secretaria_docente = group.append("g")
						.attr("transform", "translate(" + new_width/910*750 + "," + new_height/604*83  + ")")
						.attr("class", "objeto_sala");

secretaria_docente.selectAll("path")
					.data([datos_secretaria_docente])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "oficina_importante");

	secretaria_docente.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4 - new_height/604*11 - height/43) + ")")
		.text("Secretaría");

	secretaria_docente.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4  - new_height/604*11 + height/43) + ")")
		.text("Docente");

for(i = 1; i < 15; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: new_width/910*50, y: 0},
			{x: new_width/910*50, y: new_height/302*100},
			{x: 0, y: new_height/302*100},
			{x: 0, y: 0}
			];

	var sala_misteriosa = group.append("g")
							.attr("transform", "translate(" + new_width/910*i*50 + "," + new_height/302*202  + ")")
							.attr("class", "objeto_sala");

	sala_misteriosa.selectAll("path")
						.data([datos_misteriosos])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "oficina_profe");

		sala_misteriosa.append("text")
			.attr("transform", "translate(" + new_width/910*25 + "," + new_height/302*50 + ") rotate(90)")
			.text("Oficina " + (223 - i) );
}

var datos_sala_reuniones = [
		{x: 0, y: 0},
		{x: new_width/910*100, y: 0},
		{x: new_width/910*100, y: new_height/302*100},
		{x: 0, y: new_height/302*100},
		{x: 0, y: 0}
		];

var sala_reuniones = group.append("g")
						.attr("transform", "translate(" + new_width/910*15*50 + "," + new_height/302*202  + ")")
						.attr("class", "objeto_sala");

sala_reuniones.selectAll("path")
					.data([datos_sala_reuniones])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "auditorio");

	sala_reuniones.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + new_height/302*50 + ") rotate(90)")
		.text("Sala Reuniones");

//Cocina
var datos_cocina = [
		{x: 0, y: 0},
		{x: new_width/910*25, y: 0},
		{x: new_width/910*25, y: new_height/302*100},
		{x: 0, y: new_height/302*100},
		{x: 0, y: 0}
		];

var cocina = group.append("g")
						.attr("transform", "translate(" + new_width/910*16.5*50 + "," + new_height/302*177  + ")")
						.attr("class", "objeto_sala");

cocina.selectAll("path")
					.data([datos_cocina])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "otros");

	cocina.append("text")
		.attr("transform", "translate(" + new_width/910*25/2 + "," + new_height/302*50 + ") rotate(90)")
		.text("Cocina");
</script>
</div>

# Tercer Piso Edificio Poniente

<div id="mapa_3ro_piso_poniente">

<script>
var width = document.getElementById("mapa_3ro_piso_poniente").offsetWidth
var height = width*430/706


var svg = d3.select("#mapa_3ro_piso_poniente")
			.append("svg")
			.attr("width", width)
			.attr("height", height);

var group = svg.append('g')
				.attr("transform", "translate("+ width*1/20 + "," + height/43*5 + ") rotate(" + 0 + ")");

var new_height = height/43*33
var new_width = width/10*9

//Fondo del mapa
var datos_fondo = [
			{x: 0, y: 0},
			{x: new_width, y: new_height*50/302},
			{x: new_width, y: new_height},
			{x: 0, y: new_height},
			{x: 0, y: 0}
			]

group.append("g").selectAll("path")
					.data([datos_fondo])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "piso");

//Lab Eniac
var datos_lab_eniac = [
			{x: 0, y: 0},
			{x: new_width/910*100, y: new_height/302*11/2},
			{x: new_width/910*100, y: new_height/302*125},
			{x: 0, y: new_height/302*125},
			{x: 0, y: 0}
			];

var lab_eniac = group.append("g")
						.attr("transform", "translate(" + (new_width/910*50) + "," + (new_height/604*6)  + ")")
						.attr("class", "objeto_sala");

lab_eniac.selectAll("path")
			.data([datos_lab_eniac])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "sala_de_estudio");
		   
	lab_eniac.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*65 - height/43)  + ")")
			.text("Laboratorio");

	lab_eniac.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*65 + height/43)  + ")")
			.text("Eniac");                  

//Lab Colossus
var datos_lab_colossus = [
			{x: 0, y: 0},
			{x: new_width/910*100, y: new_height/302*11/2},
			{x: new_width/910*100, y: new_height/302*119},
			{x: 0, y: new_height/302*119},
			{x: 0, y: 0}
			];

var lab_colossus = group.append("g")
						.attr("transform", "translate(" + (new_width/910*150) + "," + (new_height/604*17)  + ")")
						.attr("class", "objeto_sala");

lab_colossus.selectAll("path")
			.data([datos_lab_colossus])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "posgrado");
		  
	lab_colossus.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*59 - height/43)  + ")")
			.text("Laboratorio");

	lab_colossus.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*59 + height/43)  + ")")
			.text("Colossus");                   

//Auditorio Flajolet
var datos_aud_flajolet = [
			{x: 0, y: 0},
			{x: new_width/910*100, y: new_height/302*11/2},
			{x: new_width/910*100, y: new_height/302*148},
			{x: 0, y: new_height/302*148},
			{x: 0, y: 0}
			];

var aud_flajolet = group.append("g")
						.attr("transform", "translate(" + (new_width/910*250) + "," + (new_height/302*14)  + ")")
						.attr("class", "objeto_sala");

aud_flajolet.selectAll("path")
			.data([datos_aud_flajolet])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "auditorio");

	aud_flajolet.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 - 3*height/43)  + ")")
			.text("Sala");

	aud_flajolet.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 - height/43)  + ")")
			.text("Phillipe");

	aud_flajolet.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 + height/43)  + ")")
			.text("\"Algorithmix\"");

	aud_flajolet.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 + 3*height/43)  + ")")
			.text("Flajolet");

//Lab Anakena
var datos_lab_anakena = [
			{x: 0, y: new_height/302*11/2},
			{x: new_width/910*100, y: new_height/302*11},
			{x: new_width/910*100, y: new_height/302*148},
			{x: 0, y: new_height/302*148},
			{x: 0, y: new_height/302*11/2}
			];

var lab_anakena = group.append("g")
						.attr("transform", "translate(" + (new_width/910*350) + "," + (new_height/302*14)  + ")")
						.attr("class", "objeto_sala");

lab_anakena.selectAll("path")
			.data([datos_lab_anakena])
			.enter()
			.append("path")
			.attr("d", line)
			.attr("class", "posgrado");
			 
	lab_anakena.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 - height/43)  + ")")
			.text("Laboratorio");

	lab_anakena.append("text")
			.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*74 + height/43)  + ")")
			.text("Anakena");

//Escalera
var escalera = group.append("g")
						.attr("transform", "translate(" + (new_width/910*505) + "," + (new_height/302*100)  + ")")
						.attr("class", "objeto_sala");

escalera.selectAll("circle")
			.data([[]])
			.enter()
			.append("circle")
			.attr("class", "otros")
			.style("stroke", "#1f1954")
			.attr("r", new_width/910*50)
			.attr("cx", 0)
			.attr("cy", 0);

escalera.append("text")
			.text("Escalera");

//Impresora
var datos_impresora = [
		{x: 0, y: 0},
		{x: new_width/910*50, y: 0},
		{x: new_width/910*50, y: new_height/302*50},
		{x: 0, y: new_height/302*50},
		{x: 0, y: 0}
		];

var impresora = group.append("g")
						.attr("transform", "translate(" + new_width/910*12*50 + "," + new_height/302*77  + ")")
						.attr("class", "objeto_sala");

impresora.selectAll("path")
					.data([datos_impresora])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "otros");

	impresora.append("text")
		.attr("transform", "translate(" + new_width/910*25 + "," + new_height/302*25 + ")")
		.text("Printer");

//Ada Lovelace
var datos_ada_lovelace = [
		{x: 0, y: 0},
		{x: new_width/910*100, y: new_height/302*11/2},
		{x: new_width/910*100, y: new_height/302*183/2},
		{x: 0, y: new_height/302*183/2},
		{x: 0, y: 0}
		];

var ada_lovelace = group.append("g")
						.attr("transform", "translate(" + new_width/910*650 + "," + new_height/604*72  + ")")
						.attr("class", "objeto_sala");

ada_lovelace.selectAll("path")
					.data([datos_ada_lovelace])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "auditorio");

	ada_lovelace.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4 - height*2/43) + ")")
		.text("Sala");

	ada_lovelace.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + new_height/302*183/4 + ")")
		.text("Ada");

	ada_lovelace.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4 + height*2/43) + ")")
		.text("Lovelace");

//Grace Hopper
var datos_grace_hopper = [
		{x: 0, y: 0},
		{x: new_width/910*100, y: new_height/302*11/2},
		{x: new_width/910*100, y: new_height/302*183/2 - new_height/604*11},
		{x: 0, y: new_height/302*183/2 - new_height/604*11},
		{x: 0, y: 0}
		];

var grace_hopper = group.append("g")
						.attr("transform", "translate(" + new_width/910*750 + "," + new_height/604*83  + ")")
						.attr("class", "objeto_sala");

grace_hopper.selectAll("path")
					.data([datos_grace_hopper])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "auditorio");

	grace_hopper.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4 - new_height/604*11 - height*2/43) + ")")
		.text("Sala");

	grace_hopper.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4  - new_height/604*11) + ")")
		.text("Grace");

	grace_hopper.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + (new_height/302*183/4  - new_height/604*11 + height*2/43) + ")")
		.text("Hopper");

for(i = 1; i < 15; i++){
	var datos_misteriosos = [
			{x: 0, y: 0},
			{x: new_width/910*50, y: 0},
			{x: new_width/910*50, y: new_height/302*100},
			{x: 0, y: new_height/302*100},
			{x: 0, y: 0}
			];

	var sala_misteriosa = group.append("g")
							.attr("transform", "translate(" + new_width/910*i*50 + "," + new_height/302*202  + ")")
							.attr("class", "objeto_sala");

	sala_misteriosa.selectAll("path")
						.data([datos_misteriosos])
						.enter()
						.append("path")
						.attr("d", line)
						.attr("class", "oficina_profe");

		sala_misteriosa.append("text")
			.attr("transform", "translate(" + new_width/910*25 + "," + new_height/302*50 + ") rotate(90)")
			.text("Oficina " + (324 - i) );
}

var datos_sala_sistemas = [
		{x: 0, y: 0},
		{x: new_width/910*100, y: 0},
		{x: new_width/910*100, y: new_height/302*100},
		{x: 0, y: new_height/302*100},
		{x: 0, y: 0}
		];

var sistemas = group.append("g")
						.attr("transform", "translate(" + new_width/910*15*50 + "," + new_height/302*202  + ")")
						.attr("class", "objeto_sala");

sistemas.selectAll("path")
					.data([datos_sala_sistemas])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "oficina_importante");

	sistemas.append("text")
		.attr("transform", "translate(" + new_width/910*50 + "," + new_height/302*50 + ") rotate(90)")
		.text("Sistemas");

//Datos Cocina
var datos_cocina = [
		{x: 0, y: 0},
		{x: new_width/910*25, y: 0},
		{x: new_width/910*25, y: new_height/302*100},
		{x: 0, y: new_height/302*100},
		{x: 0, y: 0}
		];

var cocina = group.append("g")
						.attr("transform", "translate(" + new_width/910*16.5*50 + "," + new_height/302*177  + ")")
						.attr("class", "objeto_sala");

cocina.selectAll("path")
					.data([datos_cocina])
					.enter()
					.append("path")
					.attr("d", line)
					.attr("class", "otros");

	cocina.append("text")
		.attr("transform", "translate(" + new_width/910*25/2 + "," + new_height/302*50 + ") rotate(90)")
		.text("Cocina");
</script>

</div>

Disclaimer: Los mapas que están aquí están hechos al ojímetro, hay salas que son de distinto tamaño en la vida real :O

Agradecimientos al Grupo de Agilidad de Madrid por la estructura de los [mapas](https://salas-uchile.herokuapp.com/).
