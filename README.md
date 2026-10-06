# Portal de cursos de verano · Prototipo v4

Universidad Continental · Modalidad A Distancia. Prototipo con datos de demostración: el ingreso, los estudiantes, la oferta, los celulares y las solicitudes son ficticios. Los datos se guardan solo en el navegador.

## Qué cambió en la v4

- **Panel rediseñado para demanda masiva:** menú lateral, filtros globales por **facultad y programa** (catálogo oficial de la modalidad A Distancia: 5 facultades y 16 programas, según ucontinental.edu.pe/facultades) que se aplican al resumen, a la demanda y a los estudiantes.
- **Resumen:** solicitudes por facultad y por programa (al tocar una barra se filtra), cursos más solicitados frente al mínimo, seguimiento y solicitudes por día.
- **Demanda por curso:** buscador, semáforo (alcanza / cerca / lejos), estado del curso, orden por demanda o cercanía al mínimo, y los programas que piden cada curso.
- **Estudiantes:** filtros rápidos (pendientes, prefieren WhatsApp, con curso abierto, asignados a mí, sin asignar), búsqueda por nombre, correo, celular o n.° de solicitud, filtros por curso, seguimiento, preferencia, ciclo y agente, tabla paginada de 25 en 25, **acciones masivas** (asignar, marcar como contactados, exportar la selección) y **ficha lateral** con contacto, cursos, costo estimado, asignación, notas e historial.
- **Asignación a agentes:** tres usuarios de mesa de ayuda de ejemplo (Ana Torres, Rosa Vega y Miguel Paz).
- **Simulación de costos en el portal:** al elegir cursos, el estudiante ve el **costo estimado** y el cronograma de **matrícula y cuotas mensuales**; también aparece en la revisión, en la confirmación y en la constancia PDF. Coordinación configura el costo por crédito, la matrícula, el número de cuotas y sus vencimientos (valores de ejemplo: S/ 120 por crédito, matrícula S/ 100 y 3 cuotas).
- **Datos de demostración:** unas 520 solicitudes ficticias repartidas por programa.

## Qué cambió en la v3

- **Escenarios de egreso al ingresar:** cuándo terminaría el estudiante sin veranos y con 1, 2 o 3 veranos consecutivos, respetando prerrequisitos.
- **Solo cursos con prerrequisitos aprobados.** Se eliminaron los grupos "Si apruebas lo que llevas ahora" y "Aún no disponibles".
- **Campaña por fases:** solicitudes abiertas → en evaluación → horarios publicados.
- **Fase 1:** el estudiante solicita la apertura de cursos sin horarios, deja su celular y su medio de contacto preferido, y puede modificar o retirar su solicitud hasta el cierre.
- **Fase 2:** en los cursos abiertos elige sección y arma su horario. Los cruces **no bloquean**: las sesiones en vivo se graban y la asistencia no es obligatoria.
- **Panel nuevo (`panel.html`)** con dos roles: mesa de ayuda y Coordinación académica.
- **Publicación anticipada de horarios (v3.1):** Coordinación puede marcar "Publicar horario ahora" en un curso abierto con secciones. Desde ese momento, los estudiantes ven sus secciones y eligen la suya sin esperar la fase de horarios; el resto de cursos sigue con "Horario por publicar". Se registra un correo automático a quienes lo solicitaron.

## Contenido

```
index.html                 Landing pública (sin planes, cursos ni oferta)
app.html                   Portal del estudiante: escenarios, malla, solicitud y horario
panel.html                 Panel de Coordinación académica y mesa de ayuda
direcciones-de-diseno.html Direcciones de diseño de Claude Design (referencia)
support.js, vendor/        Motor de las páginas de Claude Design (React y Babel incluidos)
js/config.js               Modo, rutas del backend, enlaces e imágenes
js/datos-prototipo.js      Datos de demostración (forma del contrato de API)
js/datos-panel.js          Facultades, programas y cursos por programa (demostración)
js/campana.js              Campaña (fases, fechas, mínimos, costos, cursos abiertos) y registro de solicitudes
js/api.js                  Capa de datos (prototipo o backend)
js/simulador.js            Reglas: disponibilidad, créditos, coincidencias y escenarios de egreso
js/pdf.js                  Constancia en PDF (con horario cuando ya hay secciones)
```

## Cómo publicarlo en GitHub Pages

1. En el repositorio, reemplaza todos los archivos por el contenido de esta carpeta (incluidas `vendor/` y `js/campana.js`).
2. GitHub Pages publica los cambios en uno o dos minutos.

Para abrirlo en la computadora: `npx serve .` o `python -m http.server 8000` y luego `http://localhost:8000/`.

## Roles del panel

| Función | Mesa de ayuda | Coordinación académica |
|---|:---:|:---:|
| Resumen, demanda por curso y semáforo frente al mínimo | ✅ | ✅ |
| Lista de estudiantes, filtros y exportación a Excel (CSV) | ✅ | ✅ |
| Contactar por WhatsApp, llamada o correo con mensajes ya redactados | ✅ | ✅ |
| Registrar el seguimiento y las notas de orientación | ✅ | ✅ |
| Definir el mínimo de estudiantes por curso | — | ✅ |
| Marcar cursos como abiertos o no abiertos y cargar sus secciones | — | ✅ |
| Publicar el horario de un curso antes de la fase de horarios | — | ✅ |
| Configurar fase, fechas, costos y créditos por ciclo de los escenarios | — | ✅ |
| Asignar estudiantes a agentes y acciones masivas | ✅ | ✅ |
| Simular los datos de matrícula enviados por TI | — | ✅ |

Al marcar un curso como abierto o no abierto, el sistema registra el **correo automático** a los estudiantes que lo solicitaron.

## Guion sugerido para la demostración (portal y panel en el mismo navegador)

1. **Portal · José Antonio:** muestra los escenarios de egreso. Con 1 verano no acorta, pero aligera sus ciclos; con 2 veranos termina 1 ciclo antes.
2. **Portal · María Fernanda:** sin veranos terminaría en el ciclo 11 por un curso desaprobado; con 1 verano vuelve al ciclo 10.
3. **Portal · José Antonio:** solicita la apertura de Gestión Profesional e Ingeniería Económica, revisa su celular y su preferencia, envía y descarga la constancia.
4. **Panel · Carlos Medina (Coordinación):** revisa el resumen y la demanda. Abre Gestión Profesional con dos secciones (miércoles y sábado), marca Ingeniería Económica como no abierta y, en Configuración, pasa a "Horarios publicados".
5. **Portal · José Antonio:** ve los avisos de apertura, elige su sección, mira su horario y descarga la constancia con horario.
6. **Panel · Ana Torres (mesa de ayuda):** busca a José, abre el mensaje de WhatsApp ya redactado, registra el contacto y exporta la lista a Excel.
7. **Portal · Luis Alberto:** puede solicitar, pero no enviar, por su impedimento de matrícula.

Para empezar de cero: Panel → Configuración → **Restablecer datos de demostración**.

## Notas para el piloto

- **Base de datos:** las solicitudes y la configuración pasan de `localStorage` a Supabase (plan de pago, con acceso por roles), o a la base que defina TI. Las funciones de `js/campana.js` se reemplazan por llamadas al backend.
- **WhatsApp:** en el prototipo, el enlace se abre sin destinatario porque los números son ficticios. En el piloto se abrirá el chat del estudiante con el mensaje ya redactado. Si la mesa de ayuda usa números personales, conviene evaluar más adelante un WhatsApp Business institucional, para que los mensajes salgan a nombre de la universidad y no dependan de cada persona.
- **Datos académicos:** de la API de TI. Si no llega a tiempo, plan B con carga de Excel (alumnos del piloto, cursos aprobados y oferta de verano con prerrequisitos).
- **Matrícula:** TI informará quién se matriculó en la intranet para medir el resultado de la campaña.
- **Escenarios de egreso:** por defecto usan el máximo de créditos por ciclo del plan (22 en el plan de ejemplo); Coordinación puede cambiarlo.

## Reglas que respeta el diseño

- La landing no muestra planes, cursos ni oferta.
- El tiempo de egreso siempre es una **estimación referencial**.
- No se usa "ruta recomendada" ni "recomendado para ti".
- La solicitud **no es una matrícula**: la matrícula se hace en la intranet.
- Aviso "Prototipo con datos de demostración" visible en todas las páginas.
- Contraste AA, foco visible, botones de al menos 44 px y sin desplazamiento horizontal a 375 px.
