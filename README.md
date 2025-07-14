# mallapsicologiauss
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Malla Interactiva Psicología</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Malla Interactiva – Psicología USS</h1>
    <div id="grid">
        <!-- Ejemplo para tres ramos del semestre 1 -->
        <div class="course" id="ASIGESAP01" data-prereq="">
            <button>Aprobar Estrategias para el Aprendizaje</button>
        </div>
        <div class="course" id="PSICA001" data-prereq="">
            <button>Aprobar Fund. Biológicos del Comportamiento</button>
        </div>
        <div class="course" id="PSIC8001" data-prereq="PSICA001">
            <button disabled>Aprobar Neuropsicología</button>
        </div>
        <!-- Puedes repetir este bloque con todos los cursos y prerrequisitos -->
    </div>
    <script src="script.js"></script>
</body>
</html>
