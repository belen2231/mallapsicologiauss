# mallapsicologiauss
// Lista de cursos con requisitos y datos
const courses = [
  { id: "ASIGESAP01", nombre: "Estrategias para el Aprendizaje", prereq: [] },
  { id: "FILS0001", nombre: "Antropología", prereq: [] },
  { id: "PSICA001", nombre: "Fundamentos Biológicos del Comportamiento", prereq: [] },
  { id: "PSICA002", nombre: "Procesos Cognitivos", prereq: [] },
  { id: "PSICA003", nombre: "Evolución Histórica de la Psicología", prereq: [] },
  { id: "PSICA004", nombre: "Fundamentos Filosóficos de la Psicología", prereq: [] },
  { id: "PSICA005", nombre: "Taller de Comunicación", prereq: [] },
  { id: "FILS0002", nombre: "Ética", prereq: ["FILS0001"] },
  { id: "PSIC8001", nombre: "Neuropsicología", prereq: ["PSICA001"] },
  { id: "PSICB002", nombre: "Procesos Afectivos", prereq: ["PSICA001"] },
  { id: "PSICB003", nombre: "Fund. Socioantropológicos del Comportamiento", prereq: [] },
  { id: "PSICB004", nombre: "Intro. Metodología Investigación", prereq: [] },
  { id: "PSICB005", nombre: "Taller Trabajo Grupal", prereq: [] },
  { id: "PSICC001", nombre: "Psicología Evolutiva I", prereq: ["PSICA002", "PSICB002"] },
  { id: "PSICC002", nombre: "Psicología de la Personalidad", prereq: ["PSICA002", "PSICB002"] },
  { id: "PSICC003", nombre: "Psicología Social I", prereq: ["PSICA002", "PSICB002"] },
  { id: "PSICC004", nombre: "Metodología Investigación Aplicada", prereq: ["PSICB004"] },
  { id: "PSICC005", nombre: "Taller Entrevista", prereq: [] },
  { id: "PSICD001", nombre: "Psicopatología General", prereq: ["PSICC002"] },
  { id: "PSICD002", nombre: "Psicología Evolutiva II", prereq: ["PSICC001"] },
  { id: "PSICD003", nombre: "Psicología Social II", prereq: ["PSICC003"] },
  { id: "PSICD004", nombre: "Análisis Datos Cuantitativos", prereq: ["PSICC004"] },
  { id: "PSICD005", nombre: "Evaluación Cognitiva", prereq: ["PSICC002", "PSICB002"] },
  { id: "PSICE001", nombre: "Psicopatología Infantil", prereq: ["PSICD001"] },
  { id: "PSICE002", nombre: "Teorías Psicológicas I", prereq: ["PSICA003"] },
  { id: "PSICE003", nombre: "Análisis Datos Cualitativos", prereq: ["PSICC004"] },
  { id: "PSICE004", nombre: "Evaluación Personalidad", prereq: ["PSICD005"] },
  { id: "PSICE005", nombre: "Políticas Públicas", prereq: [] },
  { id: "PSICF001", nombre: "Psicopatología Adulto", prereq: ["PSICD001"] },
  { id: "PSICF002", nombre: "Teorías Psicológicas II", prereq: ["PSICA003"] },
  { id: "PSICF003", nombre: "Evaluación Integrada", prereq: ["PSICE004"] },
  { id: "PSICF004", nombre: "Proyectos Sociales", prereq: ["PSICC004"] },
  { id: "PSICF005", nombre: "Taller Persona Psicólogo", prereq: ["PSICE004"] },
  { id: "PSICG001", nombre: "Psicoterapia Sistémica", prereq: ["PSICE002"] },
  { id: "PSICG002", nombre: "Psicoterapia Psicoanalítica", prereq: ["PSICE002"] },
  { id: "PSICG003", nombre: "Comportamiento Organizacional", prereq: ["PSICD003", "PSICE002", "PSICF002"] },
  { id: "PSICG004", nombre: "Factores Educativos", prereq: ["PSICD002", "PSICE002", "PSICF002"] },
  { id: "PSICG005", nombre: "Problemas Psicosociales", prereq: ["PSICD003", "PSICE002", "PSICF002"] },
  { id: "PSICG006", nombre: "Integración Psicología", prereq: ["PSICE002", "PSICF002"] },
  { id: "PSICH001", nombre: "Psicoterapia Cognitiva", prereq: ["PSICF002"] },
  { id: "PSICH002", nombre: "Psicoterapia Humanista", prereq: ["PSICF002"] },
  { id: "PSICH003", nombre: "Gestión Organizacional", prereq: ["PSICG003", "PSICE002", "PSICF002"] },
  { id: "PSICH004", nombre: "Gestión Escolar", prereq: ["PSICG004", "PSICE002", "PSICF002"] },
  { id: "PSICH005", nombre: "Psicología Comunitaria", prereq: ["PSICG005", "PSICE002", "PSICF002"] }
];

// Renderizado dinámico
const grid = document.getElementById("grid");

courses.forEach(course => {
  const div = document.createElement("div");
  div.className = "course";
  div.id = course.id;
  div.setAttribute("data-prereq", course.prereq.join(","));

  const button = document.createElement("button");
  button.innerText = `Aprobar ${course.nombre}`;
  if (course.prereq.length > 0) button.disabled = true;

  button.addEventListener("click", () => {
    button.disabled = true;
    button.innerText = `✓ Aprobado`;
    div.classList.add("approved");

    // Revisar desbloqueo
    courses.forEach(otherCourse => {
      const target = document.getElementById(otherCourse.id);
      if (target.classList.contains("approved")) return;

      const requirements = otherCourse.prereq;
      if (requirements.length === 0) return;

      const fulfilled = requirements.every(req => document.getElementById(req).classList.contains("approved"));
      if (fulfilled) {
        const otherButton = target.querySelector("button");
       
