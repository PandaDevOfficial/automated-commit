# Automated-Commit

Automated-Commit es un ejemplo sencillo y reutilizable de un flujo de trabajo de GitHub Actions que actualiza periódicamente un archivo (`TIMESTAMP.txt`) con la fecha y hora actuales y realiza un commit automático cuando detecta cambios.

## Descripción

Este repositorio demuestra cómo automatizar tareas rutinarias en un repositorio usando GitHub Actions. El flujo de trabajo principal:

- Clona el contenido de la rama `master`.
- Actualiza (o crea) un archivo `TIMESTAMP.txt` con la fecha y hora actuales.
- Realiza un commit si el archivo cambió.
- Empuja el commit de vuelta a la rama `master`.

El objetivo es servir como plantilla para tareas de mantenimiento automático (por ejemplo, actualizaciones periódicas, archivos de estado, o tareas programadas similares).

## Características

- Ejecutable automáticamente en schedule (cada 12 horas por defecto).
- Permite ejecución manual desde la pestaña Actions (`workflow_dispatch`).
- Configuración mínima: nombre y correo de Git configurados en el workflow.

## Estructura del flujo de trabajo

El flujo de trabajo está definido en `.github/workflows/master.yml` e incluye:

- Triggers: `schedule` (cron cada 12 horas) y `workflow_dispatch` para ejecución manual.
- Job principal: `update_commit` que se ejecuta en `ubuntu-latest`.
- Pasos: checkout, configurar Git, actualizar `TIMESTAMP.txt`, commit y push.
- Permisos: el workflow necesita permisos de escritura (default GITHUB_TOKEN suele bastar).

## Requisitos

- Un repositorio en GitHub.
- GitHub Actions habilitado en el repositorio.

## Instalación y uso

1. Usa este repositorio como plantilla (botón "Use this template") o clónalo localmente.
2. Abre `.github/workflows/master.yml` y personaliza los valores de configuración (ver sección "Configuración" abajo).
3. Haz push de los cambios a `master` para activar el workflow.

### Ejecutar manualmente

1. Ve a la pestaña `Actions` en tu repositorio.
2. Selecciona el workflow `Automated-Commit`.
3. Haz clic en "Run workflow" y confirma la rama.

## Configuración

Edite `.github/workflows/master.yml` según necesites:

- Configura las variables `GIT_USER_EMAIL` y `GIT_USER_NAME` en Settings > Secrets and variables > Variables del repositorio (opcional, si no se establecen, se usa la cuenta de GitHub Actions por defecto).
- Cambia la frecuencia del cron si necesitas otro intervalo.
- Si prefieres, cambia el nombre del archivo `TIMESTAMP.txt` por otro archivo objetivo.

Buena práctica de seguridad: utiliza el `GITHUB_TOKEN` proporcionado por Actions para los pushes automáticos; evita poner tokens de acceso personal en texto plano.

## Personalización común

- Modificar el cron: cambia la expresión en `schedule` dentro del yml.
- Cambiar el archivo objetivo: actualiza el nombre del archivo que el script escribe.
- Agregar pruebas o validaciones: inserta pasos adicionales antes del commit para validar cambios.

## Contribuir

Las contribuciones son bienvenidas:

1. Abre un issue para discutir cambios mayores.
2. Envía Pull Requests con descripciones claras.

## Soporte

Para dudas o problemas, abra un issue en la sección `Issues` del repositorio.

---

Gracias por usar Automated-Commit.

