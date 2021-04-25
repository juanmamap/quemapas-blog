# Opciones

<div>

<div>

Selección temática

<select id="tipo"><option value="" class="any">Tipología:</option> <option value="1610" class="ecle">Eclesiástico</option> <option value="1608" class="laico">Laico</option> <option value="1608" class="hospital">Hospital</option></select> <select name="subtipo_vacio" id="subtipo_vacio" class="any ecle laico hospital"><option value="any">Subtipologia:</option></select> <select id="subtipo"><option value="" class="any ecle laico hospital">Todos</option> <option value="1723" class="ecle">Edificio de culto</option> <option value="379" class="ecle">Monasterio</option> <option value="1847" class="laico">Palacio</option> <option value="990" class="laico">Fortificación</option> <option value="1851" class="hospital">Hospital</option> <option value="1856" class="laico">Casa</option></select> <select id="fecha"><option value="">Fecha interpretativa desde:</option> <option value="1000">1000</option> <option value="1050">1050</option> <option value="1100">1100</option> <option value="1150">1150</option> <option value="1200">1200</option> <option value="1250">1250</option> <option value="1300">1300</option></select> <select id="fecha2"><option value="">Fecha interpretativa hasta:</option> <option value="1050">1050</option> <option value="1100">1100</option> <option value="1150">1150</option> <option value="1200">1200</option> <option value="1250">1250</option> <option value="1300">1300</option> <option value="1350">1350</option></select> <select id="material"><option value="">Material constructivo:</option> <option value="1723">Piedra</option> <option value="379">Ladrillo</option> <option value="1847">Piedra/Ladrillo</option></select></div>

<div>

Selección espacial

<input type="text" id="filtroProvincia" onkeyup="myFunction()" placeholder="Provincia"> <input type="text" id="filtroComarca" onkeyup="myFunction()" placeholder="Área Geográfica"> <input type="text" id="filtroMunicipio" onkeyup="myFunction()" placeholder="Municipio"> <input type="text" id="filtroLocalizacion" onkeyup="myFunction()" placeholder="Localización"> <button id="f1" onclick="aplicarFiltros()">Aplicar</button></div>

</div>

<div id="txtHint">**La selección aparecera a continuación.**</div>

<script>// var map = L.map('map',{ // center: [41, 2], // zoom: 5.5, // minZoom: 6, // attributionControl: false, // se pondrá la atribución en un lugar externo // zoomControl: true // para que sea añadido en la esquina superior derecha // // }); // // var capaBase1 = L.tileLayer('http://{s}.basemaps.cartocdn.com/rastertiles/voyager_nolabels/{z}/{x}/{y}.png').addTo(map); // funcion para que los selectores cambién en funcion de la tipologia $('#tipo').change(function() { // get the class of the selected option var select_class = $("option:selected", this).attr("class"); // clone all options from the pot select var $options = $('#subtipo > option.'+select_class).clone(); // delete all of the options in the subtipo_vacio select and append // the new options $('#subtipo_vacio') .find('option') .remove() .end() .append($options); }); function aplicarFiltros() { var tipo = document.getElementById("tipo").value var subtipo = document.getElementById("subtipo").value if (tipo == "" && subtipo == "") { document.getElementById("txtHint").innerHTML = ""; return; } else { var xmlhttp = new XMLHttpRequest(); xmlhttp.onreadystatechange = function() { if (this.readyState == 4 && this.status == 200) { document.getElementById("txtHint").innerHTML = this.responseText; } }; xmlhttp.open("GET","query/consultabd.php?tipo="+tipo+"&subtipo="+subtipo,true); //xmlhttp.open("GET","query/consultabd.php?id2="+subtipo,true); xmlhttp.send(); } }</script>
