# PlanetApp
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>PLANETAPP</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Bauhaus+93&display=swap');

        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        header {
            text-align: center;
            margin-top: 20px;
        }

        h1 {
            font-family: 'Bauhaus 93', sans-serif;
            font-size: 20px;
            text-transform: uppercase;
        }

        h2 {
            font-family: 'Bauhaus 93', sans-serif;
            font-size: 15px;
            margin: 5px 0;
        }

        .nombres {
            font-family: 'Bauhaus 93', sans-serif;
            font-size: 12px;
            position: absolute;
            top: 90px;
            right: 20px;
            width: 300px;
            text-align: right;
        }

        .actividades-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 150px;
            gap: 15px;
        }

        .actividad {
            border: 2px solid black;
            border-radius: 10px;
            padding: 15px;
            width: 80%;
            max-width: 600px;
            font-family: Arial, sans-serif;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .opciones {
            margin-top: 10px;
            display: none;
        }

        .actividad.seleccionada .opciones {
            display: block;
        }

        .completado {
            background-color: lightgreen;
            border-color: green;
        }

        .no-completado {
            border-color: red;
        }

        .contador {
            position: fixed;
            bottom: 10px;
            right: 20px;
            font-size: 14px;
            font-weight: bold;
        }

        button {
            margin-right: 5px;
            padding: 4px 8px;
            font-size: 12px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <header>
        <h1>PLANETAPP</h1>
        <h2>Cuidar el planeta es cuidar tu salud</h2>
    </header>

    <div class="nombres">
        El parris, Pollin, El nefas, El manos locas, Momito medina y El kimba
    </div>

    <div class="actividades-container">
        <div class="actividad" id="actividad1">
            Lunes: Regar una planta. (100 puntos)
            <div class="opciones">
                <button onclick="marcarCompletado(this, 1)">Completado</button>
                <button onclick="marcarNoCompletado(this, 1)">No completado</button>
            </div>
        </div>

        <div class="actividad" id="actividad2">
            Martes: Desconecta el cargador de tu celular o laptop tan pronto como termines de usarlos. (100 puntos)
            <div class="opciones">
                <button onclick="marcarCompletado(this, 2)">Completado</button>
                <button onclick="marcarNoCompletado(this, 2)">No completado</button>
            </div>
        </div>

        <div class="actividad" id="actividad3">
            Miércoles: Desconecta el cargador de tu celular o laptop tan pronto como termines de usarlos. (100 puntos)
            <div class="opciones">
                <button onclick="marcarCompletado(this, 3)">Completado</button>
                <button onclick="marcarNoCompletado(this, 3)">No completado</button>
            </div>
        </div>

        <div class="actividad" id="actividad4">
            Jueves: Lleva siempre tu bolsa de tela al supermercado para evitar las bolsas de plástico. (100 puntos)
            <div class="opciones">
                <button onclick="marcarCompletado(this, 4)">Completado</button>
                <button onclick="marcarNoCompletado(this, 4)">No completado</button>
            </div>
        </div>

        <div class="actividad" id="actividad5">
            Viernes: Apaga la pantalla de tu computadora si vas a estar un rato fuera. Vístete con ropa adecuada para no abusar de la calefacción o el aire acondicionado. (100 puntos)
            <div class="opciones">
                <button onclick="marcarCompletado(this, 5)">Completado</button>
                <button onclick="marcarNoCompletado(this, 5)">No completado</button>
            </div>
        </div>
    </div>

    <div class="contador" id="contador">
        Puntos: 0
    </div>

    <script>
        let puntos = 0;
        const estados = {};

        function marcarCompletado(btn, id) {
            const actividad = document.getElementById('actividad' + id);
            if (estados[id] !== 'completado') {
                if (estados[id] === 'no-completado') {
                    actividad.classList.remove('no-completado');
                }
                actividad.classList.add('completado');
                puntos += 100;
                actualizarContador();
                estados[id] = 'completado';
            }
        }

        function marcarNoCompletado(btn, id) {
            const actividad = document.getElementById('actividad' + id);
            if (estados[id] === 'completado') {
                puntos -= 100;
                actividad.classList.remove('completado');
            }
            actividad.classList.add('no-completado');
            actualizarContador();
            estados[id] = 'no-completado';
        }

        function actualizarContador() {
            document.getElementById('contador').innerText = `Puntos: ${puntos}`;
        }

        // Mostrar opciones al hacer clic en cada recuadro
        document.querySelectorAll('.actividad').forEach(item => {
            item.addEventListener('click', function () {
                this.classList.toggle('seleccionada');
            });
        });
    </script>

</body>
</html>