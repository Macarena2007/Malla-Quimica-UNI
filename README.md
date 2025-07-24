<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Malla Curricular - Química UNI</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #ffe6f0;
      color: #3e1f47;
      margin: 0;
      padding: 20px;
    }

    h1 {
      text-align: center;
      color: #4a1c40;
    }

    .ciclo {
      margin: 30px 0;
    }

    .ciclo h2 {
      color: #a03c7f;
      border-left: 6px solid #d36fa8;
      padding-left: 10px;
    }

    .contenedor-cursos {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .curso {
      background: #ffe6fa;
      border: 1px solid #c48fb2;
      border-radius: 10px;
      padding: 12px;
      cursor: pointer;
      flex: 1 1 180px;
      box-shadow: 1px 1px 5px rgba(0,0,0,0.1);
      transition: background 0.3s;
    }

    .curso:hover {
      background: #f9d3ec;
    }

    .no-habilitado {
      background: #e4d0f4 !important;
      border: 1px solid #a88fc4 !important;
      color: #5a3a78;
      cursor: not-allowed;
      opacity: 0.6;
    }

    .completado {
      text-decoration: line-through;
      background: #d5ffd5 !important;
      border-color: #88cc88 !important;
      color: #2f6e2f;
    }

    .nombre-curso {
      font-weight: bold;
    }

    .creditos {
      font-size: 0.9em;
      color: #555;
    }
  </style>
</head>
<body>

<h1>Malla Curricular - Ingeniería Química UNI</h1>

<!-- CICLOS DEL 1 AL 10 -->
<!-- Aquí irán todos los cursos -->
<script>
  const cursosPorCiclo = {
    "Ciclo 1": [
      ["BMA01", "Cálculo Diferencial", 5, "-", "completado"],
      ["BFI01", "Física I", 5, "-", "normal"],
      ["BMA03", "Álgebra Lineal", 4, "-", "no-habilitado"],
      ["BIC01", "Intro. a la Computación", 2, "-", "completado"],
      ["BQU01", "Química I", 5, "-", "normal"]
    ],
    "Ciclo 2": [
      ["BEF01", "Ética y Filosofía Política", 2, "-", "normal"],
      ["BEG01", "Economía General", 3, "-", "normal"],
      ["BMA02", "Cálculo Integral", 5, "BMA01", "no-habilitado"],
      ["BRC01", "Redacción y Comunicación", 2, "-", "normal"],
      ["BRN01", "Realidad Nacional", 3, "-", "normal"],
      ["CQ102", "Química Experimental", 2, "-", "normal"],
      ["CQ132", "Química Ciencia y Tecnología", 2, "-", "normal"]
    ]
    // Puedes seguir agregando más ciclos aquí si deseas
  };

  const container = document.body;

  for (const ciclo in cursosPorCiclo) {
    const divCiclo = document.createElement("div");
    divCiclo.className = "ciclo";
    divCiclo.innerHTML = `<h2>${ciclo}</h2><div class="contenedor-cursos"></div>`;
    const cursoCont = divCiclo.querySelector(".contenedor-cursos");

    cursosPorCiclo[ciclo].forEach(([cod, nombre, cred, pre, estado]) => {
      const clase = estado === "normal" ? "curso" : `curso ${estado}`;
      const div = document.createElement("div");
      div.className = clase;
      if (estado !== "no-habilitado") {
        div.setAttribute("onclick", `verCurso('${cod}', '${nombre}', ${cred}, '${pre}')`);
      }
      div.innerHTML = `
        <div class="nombre-curso">${nombre}</div>
        <div class="creditos">${cred} créditos</div>
      `;
      cursoCont.appendChild(div);
    });

    container.appendChild(divCiclo);
  }

  function verCurso(codigo, nombre, creditos, prerequisitos) {
    alert(`📘 ${nombre}\nCódigo: ${codigo}\nCréditos: ${creditos}\nPrerequisitos: ${prerequisitos}`);
  }
</script>

</body>
</html>
