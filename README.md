# Conector personalizado para la API REST v3 de Jira

Este repositorio contiene un conector personalizado para operar sobre la API REST v3 de Jira. El objetivo principal es facilitar la integración y automatización de tareas con Jira mediante funciones específicas.

## Características
- Permite realizar operaciones básicas sobre la API REST v3 de Jira.
- Se irán añadiendo funciones avanzadas de consulta y operaciones básicas conforme avance el desarrollo.
- El proyecto está en desarrollo activo.

## Uso
1. Clona este repositorio.
2. Importa el archivo `connector.json` en tu framework preferido. Por ejemplo, en Power Apps:
	- Ve a la sección de "Conectores personalizados".
	- Selecciona "Importar un conector personalizado".
	- Elige el archivo `connector.json` y sigue las instrucciones para completar la importación.
	- Configura la autenticación y los parámetros necesarios según tu entorno de Jira.
3. Una vez importado, utiliza las acciones y funciones del conector desde tu aplicación en Power Apps para interactuar con la API REST v3 de Jira.

## Limitaciones Conocidas

### Operaciones POST y la protección XSRF de Jira

Al utilizar este conector personalizado directamente desde una aplicación de navegador como Power Apps, las operaciones que modifican datos (como `POST` para añadir comentarios) fallarán debido a las medidas de seguridad de Jira (XSRF - Cross-Site Request Forgery). La API de Jira Cloud requiere un encabezado `X-Atlassian-Token: no-check` para estas solicitudes, pero los navegadores web no permiten que un conector personalizado de origen cruzado agregue este encabezado por razones de seguridad.

Esto significa que las operaciones `GET` (lectura de datos) funcionarán perfectamente, pero las operaciones `POST`, `PUT` o `DELETE` no son posibles a través de este método directo.

### Solución Recomendada

Para casos de uso que requieran modificar datos en Jira (como agregar comentarios, crear incidencias, etc.) desde un agente o una aplicación, se recomienda utilizar una capa de middleware que pueda realizar la llamada de servidor a servidor. Una excelente opción para esto es el **Atlassian Remote MCP Server**, que está diseñado para estos escenarios.

Puedes encontrar más información sobre cómo empezar aquí: [Getting started with the Atlassian Remote MCP server](https://support.atlassian.com/atlassian-rovo-mcp-server/docs/getting-started-with-the-atlassian-remote-mcp-server/).

## Estado del proyecto
Actualmente en desarrollo. Próximamente se agregarán más funciones para consultas avanzadas y operaciones sobre Jira.

## Contribuciones
Las contribuciones son bienvenidas. Si tienes ideas o mejoras, por favor abre un issue o envía un pull request.

## Licencia
Este proyecto se distribuye bajo la licencia MIT.
