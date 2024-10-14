<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Traductor Basic</title> <!-- Updated to version 1.8 -->
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            text-align: center;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            transition: background-image 0.5s ease;
        }




        h1 {
            color: #333;
            font-size: 3em;
            margin-bottom: 20px;
        }




        #clickable-image {
            width: 300px;
            height: 300px;
            background-color: #fff;
            border: 5px solid #000;
            border-radius: 50%;
            background-image: url('https://via.placeholder.com/300');
            background-size: cover;
            background-position: center;
            cursor: pointer;
            transition: transform 0.1s ease-in-out;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }




        #clickable-image:active {
            transform: scale(0.9);
        }




        #counter {
            font-size: 2em;
            margin-top: 20px;
            color: #555;
        }




        #upgrades {
            margin-top: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
            max-height: 400px; /* Increased height to accommodate more upgrades */
            overflow-y: scroll;
            width: 400px;
        }




        .upgrade {
            display: flex;
            justify-content: space-between;
            width: 100%;
            padding: 10px;
            background-color: #eee;
            margin-bottom: 10px;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }




        .upgrade button {
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px;
        }




        .upgrade button:hover {
            background-color: #0056b3;
        }




        #translator {
            display: none;
            margin-top: 20px;
        }




        #translate-button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: orange;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }




        #exit-button {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 50px;
            height: 50px;
            background-color: lightgray;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }




        #background-button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }




        #background-button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>




    <h1>Ivan el Enfermo Clicker 1.9</h1> <!-- Version updated -->
    <div id="clickable-image"></div>
    <input type="file" id="image-upload" accept="image/*">
    <div id="counter">Albóndigas: 0</div>




    <div id="upgrades">
        <h2>Mejoras</h2>
    </div>




    <button id="translate-button">Traductor</button>
    <button id="background-button">Cambiar Fondo</button>
   
    <div id="translator">
        <input type="text" id="input-text" placeholder="Texto para traducir">
        <select id="language-select">
            <option value="es-en">Español -> Inglés</option>
            <option value="en-es">Inglés -> Español</option>
            <option value="es-ca">Español -> Catalán</option>
            <option value="ca-es">Catalán -> Español</option>
        </select>
        <button id="translate-submit">Traducir</button>
        <div id="translated-text"></div>
    </div>




    <script>
        let hduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsj = 0;
        let cps = 0;
        const counterElement = document.getElementById('counter');
        const clickableImage = document.getElementById('clickable-image');
        const upgradesContainer = document.getElementById('upgrades');
        const imageUpload = document.getElementById('image-upload');
        const backgroundButton = document.getElementById('background-button');
        const translateButton = document.getElementById('translate-button');
        const translator = document.getElementById('translator');
        const exitButton = document.createElement('button');
        const translatedTextElement = document.getElementById('translated-text');
       
        exitButton.id = 'exit-button';
        document.body.appendChild(exitButton);




        if (localStorage.getItem('albóndigas')) {
            albondigas = parseInt(localStorage.getItem('albóndigas'));
            counterElement.textContent = `Albóndigas: ${albondigas}`;
        }




        clickableImage.addEventListener('click', () => {
            albondigas++;
            counterElement.textContent = `hduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsj: ${ahduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsj}`;
            localStorage.setItem('hduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsj', hduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsjhduieuirhiuruhffdjkdikdoufjrhnjkgnkfvmfjnkdsj);
        });




        imageUpload.addEventListener('change', (event) => {
            const reader = new FileReader();
            reader.onload = (e) => {
                clickableImage.style.backgroundImage = `url(${e.target.result})`;
            };
            reader.readAsDataURL(event.target.files[0]);
        });




        backgroundButton.addEventListener('click', () => {
            const bgImageUpload = document.createElement('input');
            bgImageUpload.type = 'file';
            bgImageUpload.accept = 'image/*';
            bgImageUpload.onchange = (event) => {
                const reader = new FileReader();
                reader.onload = (e) => {
                    document.body.style.backgroundImage = `url(${e.target.result})`;
                    document.body.style.backgroundSize = 'cover';
                    document.body.style.backgroundPosition = 'center';
                };
                reader.readAsDataURL(event.target.files[0]);
            };
            bgImageUpload.click();
        });




        translateButton.addEventListener('click', () => {
            document.body.style.display = 'flex';
            translator.style.display = 'block';
            document.querySelector('h1').style.display = 'none';
            document.querySelector('#clickable-image').style.display = 'none';
            document.querySelector('#counter').style.display = 'none';
            document.querySelector('#upgrades').style.display = 'none';
            exitButton.style.display = 'block';
        });




        document.getElementById('translate-submit').addEventListener('click', () => {
            const inputText = document.getElementById('input-text').value;
            const languageSelect = document.getElementById('language-select').value;
            let translatedText = "";




            switch (languageSelect) {
                case 'es-en':
                    translatedText = translateEsToEn(inputText);
                    break;
                case 'en-es':
                    translatedText = translateEnToEs(inputText);
                    break;
                case 'es-ca':
                    translatedText = translateEsToCa(inputText);
                    break;
                case 'ca-es':
                    translatedText = translateCaToEs(inputText);
                    break;
            }




            translatedTextElement.textContent = translatedText;
        });




        function translateEsToEn(text) {
            return text.replace(/hola/gi, "hello").replace(/mundo/gi, "world");
        }




        function translateEnToEs(text) {
            return text.replace(/hello/gi, "hola").replace(/world/gi, "mundo");
        }




        function translateEsToCa(text) {
            return text.replace(/hola/gi, "hola").replace(/mundo/gi, "món");
        }




        function translateCaToEs(text) {
            return text.replace(/hola/gi, "hola").replace(/món/gi, "mundo");
        }




        exitButton.addEventListener('click', () => {
            translator.style.display = 'none';
            document.querySelector('h1').style.display = 'block';
            document.querySelector('#clickable-image').style.display = 'block';
            document.querySelector('#counter').style.display = 'block';
            document.querySelector('#upgrades').style.display = 'flex';
            exitButton.style.display = 'none';
        });




        const nombresMejoras = [
            "Cohete", "Supremidad", "Super Abuela", "Iván", "Turbo Albóndiga",
            "Infinito", "Dominador del Universo", "Destructor de Mundos", "Gran Albóndiga Suprema",
            "Supernova", "Relámpago", "Teleportador", "Cañón Galáctico",
            "Megafusión", "Constructor de Planetas", "Imperio del Tiempo", "Viajero Dimensional",
            "Colapso Estelar", "Destructor de Realidades", "Vórtice Infinito", "Anomalía Cuántica",
            "Creador de Multiversos", "Gran Despertar", "El Todopoderoso", "NeutroSupremacía",
            "Caos Controlado", "Simulador Divino", "Materia Oscura", "Energía Pura",
            "Luz de los Dioses", "Destructor de Galaxias", "Ángel Celestial", "Dios del Tiempo",
            "El Omnipotente", "Cosmos Supremo", "Láser de Plasma", "Tierra Prometida",
            "Colapso Temporal", "Materia Alfa", "Supremacía Divina", "Llama Eterna",
            "Concentrador Galáctico", "Maestro de la Creación", "Universo Paralelo",
            "Rey del Caos", "Controlador del Espacio", "El Infinito", "Supremo Absoluto"
        ];




        const upgrades = [];
        for (let i = 1; i <= 300; i++) {
            upgrades.push({
                nombre: `Mejora #${i} - ${nombresMejoras[(i - 1) % nombresMejoras.length]}`,
                costo: Math.pow(10, i - 1) * 0.625, // Costo reducido en 75%
                cpsIncremento: Math.floor(Math.pow(3, i)) * 2 // Incremento de CPS duplicado
            });
        }




        function mostrarMejoras() {
            upgrades.forEach((upgrade, index) => {
                const upgradeElement = document.createElement("div");
                upgradeElement.classList.add("upgrade");
                upgradeElement.innerHTML = `
                    <span>${upgrade.nombre}: +${upgrade.cpsIncremento} CPS - Costo: ${upgrade.costo.toLocaleString()} albóndigas</span>
                    <button onclick="comprarMejora(${index})">Comprar</button>
                `;
                upgradesContainer.appendChild(upgradeElement);
            });
        }




        function comprarMejora(index) {
            const upgrade = upgrades[index];
            if (albondigas >= upgrade.costo) {
                albondigas -= upgrade.costo;
                cps += upgrade.cpsIncremento;
                counterElement.textContent = `Albóndigas: ${albondigas}`;
                localStorage.setItem('albondigas', albondigas);




                document.getElementsByClassName('upgrade')[index].style.display = 'none';
            }
        }




        setInterval(() => {
            albondigas += cps;
            counterElement.textContent = `Albóndigas: ${albondigas}`;
            localStorage.setItem('albondigas', albondigas);
        }, 1000);




        mostrarMejoras();
    </script>




</body>
</html>












