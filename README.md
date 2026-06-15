

Proyecto Final – Pruebas de Carga y Rendimiento
Curso: Testing y Validación de Software
Maestría en Ingeniería de Software – Universidad de La Sabana
2026-1

Integrantes:
- Andrés Meneses Ortega
- David Hernando Monsalve
- Sergio Cruz Triana


# NOTA: Toda la documentación en la WIKI del repositorio
[WIKI](https://github.com/sergioing1000/TYVS-Proyecto_Pruebas_carga_y_rendimiento/wiki)

# Proyecto de Pruebas de Calidad, Integración y Rendimiento

## Descripción General

Este proyecto tiene como objetivo implementar buenas prácticas de aseguramiento de calidad de software mediante la construcción de una solución Java basada en Maven, incorporando:

* Pruebas unitarias.
* Pruebas de integración.
* Automatización CI/CD.
* Contenerización con Docker.
* Pruebas de rendimiento utilizando k6.
* Ejecución automatizada mediante GitHub Actions.

La solución permite validar la calidad funcional y no funcional de la aplicación durante todo el ciclo de desarrollo.

---

# Tecnologías Utilizadas

## Desarrollo

* Java
* Maven

## Testing

* JUnit
* Mockito

## Automatización

* GitHub Actions
* Jenkins

## Contenerización

* Docker

## Pruebas de Rendimiento

* k6

---

# Estructura del Proyecto

```text
project-root/
│
├── src/
│   ├── main/
│   │   └── java/
│   │       └── ...
│   │
│   └── test/
│       └── java/
│           └── ...
│
├── performance/
│   └── voter-regression.js
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── Dockerfile
├── Jenkinsfile
├── pom.xml
└── README.md
```

---

# Funcionalidades Implementadas

## 1. Pruebas Unitarias

Se implementaron pruebas unitarias utilizando:

* JUnit
* Mockito

Objetivos:

* Validar la lógica de negocio.
* Simular dependencias externas mediante mocks.
* Verificar comportamientos esperados y manejo de excepciones.

### Casos cubiertos

* Flujo exitoso.
* Validación de entradas.
* Manejo de errores.
* Simulación de fallos del repositorio.
* Verificación de excepciones controladas.

---

## 2. Pruebas de Integración

Se desarrollaron pruebas de integración para validar la interacción entre los diferentes componentes del sistema.

### Escenarios evaluados

* Comunicación entre servicios.
* Integración con repositorios.
* Flujo completo de ejecución.
* Manejo de errores durante operaciones de persistencia.

---

## 3. Simulación de Fallos

Con el fin de aumentar la cobertura de pruebas se implementó una clase auxiliar:

```java
FakeRepository
```

Esta clase permite simular:

* Errores de conexión.
* Fallos inesperados.
* Excepciones lanzadas por la capa de persistencia.

Beneficios:

* Mayor robustez de las pruebas.
* Validación de escenarios negativos.
* Incremento de cobertura funcional.

---

# Construcción del Proyecto

## Compilar

```bash
mvn clean compile
```

## Ejecutar pruebas

```bash
mvn clean test
```

Resultado esperado:

```text
BUILD SUCCESS
Tests run: 7
Failures: 0
Errors: 0
Skipped: 0
```

---

# Integración Continua (CI)

Se configuró GitHub Actions para automatizar la ejecución de pruebas.

## Workflow

Archivo:

```text
.github/workflows/main.yml
```

### Activación

* Push al repositorio.
* Pull Requests.

### Actividades ejecutadas

1. Checkout del código.
2. Configuración de Java.
3. Compilación Maven.
4. Ejecución de pruebas unitarias.
5. Ejecución de pruebas de integración.
6. Ejecución de pruebas de rendimiento con k6.

---

# Pruebas de Rendimiento

Se implementaron pruebas de carga utilizando k6.

## Objetivos

* Validar tiempos de respuesta.
* Medir estabilidad bajo carga.
* Detectar cuellos de botella.

### Ejecución local

```bash
k6 run performance/voter-regression.js
```

### Métricas observadas

* Tiempo de respuesta.
* Throughput.
* Errores HTTP.
* Usuarios virtuales concurrentes.

---

# Dockerización

Se agregó soporte para Docker.

## Construir imagen

```bash
docker build -t voter-app .
```

## Ejecutar contenedor

```bash
docker run -p 8080:8080 voter-app
```

Beneficios:

* Portabilidad.
* Entornos reproducibles.
* Despliegue simplificado.

---

# Pipeline de Entrega Continua (CD)

Se definió un pipeline Jenkins que incluye:

1. Clonar repositorio.
2. Construir aplicación.
3. Ejecutar pruebas.
4. Construir imagen Docker.
5. Publicar imagen en registro Docker.
6. Preparar despliegue.

Archivo:

```text
Jenkinsfile
```

---

# Resultados Obtenidos

## Calidad

✅ Pruebas unitarias implementadas

✅ Pruebas de integración implementadas

✅ Manejo de excepciones validado

✅ Simulación de fallos de infraestructura

---

## Automatización

✅ GitHub Actions configurado

✅ Pipeline CI funcional

✅ Ejecución automática de pruebas

---

## Rendimiento

✅ Scripts k6 implementados

✅ Pruebas de carga automatizadas

✅ Ejecución desde GitHub Actions

---

## DevOps

✅ Dockerfile creado

✅ Jenkinsfile configurado

✅ Base para pipeline CI/CD completa

---

# Próximas Mejoras

* Generación automática de reportes HTML.
* Integración con SonarQube.
* Medición de cobertura con JaCoCo.
* Publicación automática de artefactos.
* Despliegue automatizado a ambientes cloud.
* Monitoreo de métricas mediante Grafana y Prometheus.

---

# Autor

Proyecto desarrollado como ejercicio práctico de:

* Testing de Software.
* Integración Continua (CI).
* Entrega Continua (CD).
* Pruebas de Rendimiento.
* DevOps y Automatización.
