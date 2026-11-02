# Sistema de Gestión de Distribución y Logística Asistido con IA

**Trabajo Práctico Integrador y Progresivo – Entrega N.º 4**  
**Asignatura:** Organización Empresarial  
**Carrera:** Tecnicatura Universitaria en Programación – UTN  
**Institución:** Universidad Tecnológica Nacional  

**Alumno:** Franco Aguerre Laciar  
**Docente titular:** Gabriela Martínez  

---

## 1. Accesos al proyecto

- **Repositorio GitHub:** https://github.com/FrancoAguerre/tpi-organizacion-empresarial-cocacola
- **Tablero de gestión (GitHub Projects / Jira):** 

---

## 2. Descripción del proyecto

El presente proyecto propone el desarrollo de un **Sistema de Gestión de Distribución y Logística asistido con Inteligencia Artificial** para The Coca-Cola Company.

La solución consiste en un módulo de software destinado a optimizar la planificación de rutas de distribución desde una planta embotelladora hacia las distintas distribuidoras.

El sistema utiliza información histórica de pedidos, demanda y disponibilidad de vehículos para generar predicciones y sugerencias de rutas optimizadas, considerando las restricciones operativas de la planta.

Desde la perspectiva de los sistemas de información, se trata de un **Sistema de Soporte de Decisiones (DSS)**: procesa datos operativos y los transforma en información útil para facilitar la toma de decisiones. La aprobación definitiva de las rutas permanece bajo responsabilidad del planificador de logística.

### Alcance

La implementación contempla inicialmente una prueba piloto en una planta ubicada en Argentina (Planta Piloto), con posibilidad de extender posteriormente la solución a una segunda planta del país.

### Objetivo general

Desarrollar e implementar un módulo inteligente que permita mejorar la planificación logística, reducir los costos operativos y optimizar la asignación de vehículos y rutas de distribución mediante el análisis de datos históricos y modelos predictivos.

---

## 3. Tecnologías y herramientas previstas

| Tecnología | Aplicación dentro del proyecto |
|---|---|
| Python | Desarrollo de la lógica principal del sistema. |
| PostgreSQL | Almacenamiento y administración de datos. |
| scikit-learn | Desarrollo y evaluación de modelos predictivos. |
| OR-Tools | Optimización matemática y planificación de rutas. |
| OpenStreetMap | Información geográfica para el cálculo de recorridos. |
| Git | Control de versiones del proyecto. |
| GitHub | Repositorio y colaboración. |
| GitHub Projects | Seguimiento de tareas e historias de usuario. |

---

## 4. Modelado del proceso de negocio (BPMN)

El proceso modelado representa la planificación y ejecución de las rutas de distribución de la Planta Piloto.

El objetivo es transformar el procedimiento tradicional de planificación manual en un proceso asistido por un sistema inteligente, manteniendo la intervención humana en las decisiones críticas.

### Actores y responsabilidades

El proceso contempla los siguientes participantes:

- **Planta Piloto:** organización donde se desarrolla y ejecuta el proceso.
- **Área de Logística:** responsable de gestionar pedidos y planificar las distribuciones.
- **Planificador de Logística:** analiza las sugerencias del sistema y aprueba las rutas.
- **Área de Sistemas:** responsable de la infraestructura, integración y disponibilidad de los datos.
- **Sistema de Gestión Logística:** procesa los datos, estima la demanda y genera propuestas de rutas.
- **Distribuidoras:** destinatarias de los pedidos y entregas.

### Flujo general del proceso

1. Se reciben los pedidos de las distribuidoras.
2. Se consultan los datos históricos y la información de disponibilidad de vehículos.
3. El sistema verifica la integridad y disponibilidad de los datos necesarios.
4. Se procesan los datos y se estima la demanda por distribuidora.
5. El algoritmo de optimización genera una propuesta de rutas considerando la capacidad de los vehículos y las restricciones operativas.
6. El planificador analiza la propuesta.
7. Si la propuesta es aprobada, se asignan los pedidos y vehículos correspondientes.
8. Si es rechazada, se revisan los parámetros y se genera una nueva propuesta.
9. Se ejecutan las entregas.
10. Se registran los resultados reales para evaluar el desempeño y retroalimentar el modelo.

### Decisiones y excepciones

El proceso contempla las siguientes situaciones:

- Datos incompletos o inconsistentes: se solicita su corrección antes de continuar.
- Vehículos no disponibles: se excluyen de la planificación.
- Capacidad insuficiente: se requiere una nueva distribución de pedidos o asignación de vehículos.
- Ruta rechazada por el planificador: se revisan los parámetros y se vuelve a ejecutar la optimización.
- Entrega ejecutada: se registran los kilómetros reales y se comparan con los estimados.

---

## 5. Historias de usuario y gestión del backlog

Las historias de usuario permiten representar las funcionalidades principales desde la perspectiva de quienes interactúan con el sistema.

Se utilizará GitHub Projects para organizar las actividades y visualizar su estado de avance.


## 6. Estructura de datos

El diccionario de datos definido en la Entrega N.º 3 establece tres entidades principales que representan el funcionamiento central del sistema.

| Entidad | Descripción |
|---|---|
| PEDIDO | Representa las solicitudes de entrega de las distribuidoras. |
| VEHÍCULO | Representa los recursos disponibles para realizar las entregas. |
| RUTA | Representa la planificación diaria de distribución y los recorridos asignados. |

### Relaciones principales

- Una RUTA puede agrupar varios PEDIDOS.
- Una RUTA utiliza un único VEHÍCULO por jornada.
- Un VEHÍCULO puede participar en diferentes RUTAS a lo largo del tiempo.
- Cada PEDIDO corresponde a una distribuidora.

Estas entidades permiten organizar los datos de entrada, las restricciones operativas y las salidas generadas por el sistema.

---

## 7. Indicadores de control y estándares de desempeño

Se establecen indicadores cuantitativos para evaluar el funcionamiento del sistema y determinar si se cumplen los objetivos definidos durante la planificación del proyecto.

| Indicador | Estándar esperado | Método de evaluación |
|---|---|---|
| Escalabilidad de registros | Procesar al menos 1.000.000 de registros históricos. | Pruebas de carga y consultas. |
| Tiempo de respuesta del MVP | 15 segundos o menos. | Medición de consultas en pantalla. |
| Tiempo de respuesta de versión final | 5 segundos o menos. | Pruebas de rendimiento. |
| Precisión del modelo predictivo | MAPE igual o menor al 15 %. | Comparación entre demanda estimada y real. |
| Eficiencia operativa | Reducir al menos un 10 % los kilómetros recorridos. | Comparación con la planificación manual. |
| Cumplimiento de planificación | Piloto operativo desde el 17/05/2027. | Verificación de hitos del cronograma. |

### Mecanismos de control

El control del proyecto se realizará mediante:

1. **Control de calidad de datos:** verificar que los pedidos y registros históricos sean completos y consistentes.
2. **Control de rendimiento:** medir los tiempos de respuesta y la capacidad de procesamiento.
3. **Control predictivo:** comparar las estimaciones de demanda con los resultados reales mediante el indicador MAPE.
4. **Control de eficiencia logística:** comparar los kilómetros recorridos con los de la planificación manual.
5. **Control de aprobación:** registrar la validación de las rutas por parte del planificador.

### Acciones correctivas

Cuando los resultados obtenidos no alcancen los estándares establecidos, se deberán analizar las causas del desvío y aplicar medidas correctivas.

Algunos ejemplos son:

- Mejorar la calidad de los datos históricos.
- Ajustar los parámetros del modelo predictivo.
- Revisar las restricciones del algoritmo de optimización.
- Optimizar las consultas y operaciones de la base de datos.
- Revisar la asignación de vehículos y pedidos.

---

## 8. Control de versiones y trabajo colaborativo

El proyecto utiliza Git y GitHub para administrar los cambios, mantener un historial de versiones y facilitar la revisión de las modificaciones realizadas.

### Estrategia de ramas

Se establece la siguiente organización:

- `main`: rama principal con documentación revisada y aprobada.
- `develop`: rama de integración de cambios.
- `feature/*`: ramas secundarias destinadas al desarrollo de funcionalidades o documentación específica.

### Convención de commits

Los mensajes de commit deberán ser claros, descriptivos y representar el cambio realizado.

Ejemplos:

- `docs: add project overview to README`
- `docs: add BPMN process documentation`
- `feat: define logistics user stories`
- `docs: add performance indicators`
- `fix: correct data dictionary references`

### Pull Requests

Las modificaciones realizadas en ramas secundarias deberán incorporarse mediante Pull Requests.

El procedimiento contempla:

1. Crear una rama secundaria.
2. Realizar los cambios correspondientes.
3. Registrar los cambios mediante commits descriptivos.
4. Crear un Pull Request hacia la rama correspondiente.
5. Revisar las modificaciones y solicitar correcciones cuando sea necesario.
6. Aprobar y fusionar los cambios.

Se deberá conservar evidencia de al menos un Pull Request con revisión de pares y resolución documentada.

---

## 9. Estructura del repositorio

La documentación del proyecto se organizará de la siguiente manera:

```text
sistema-gestion-logistica/
│
├── README.md
│
├── docs/
│   ├── bpmn/
│   │   └── proceso_logistico.bpmn
│   │
│   ├── entregas/
│   │   ├── entrega_1.pdf
│   │   ├── entrega_2.pdf
│   │   └── entrega_3.pdf
│   │
│   └── modelo_datos/
│       └── diccionario_datos.md
│
├── src/
│   ├── prediccion/
│   ├── optimizacion/
│   └── integracion/
│
└── tests/
    ├── test_prediccion.py
    └── test_optimizacion.py
```

Esta estructura permite separar la documentación académica, los diagramas, los componentes del sistema y las pruebas técnicas.

---

