# Informe: Git, GitHub, Tailscale y Gitea

**Equipo:** [número]  
**Asignatura:** [nombre de la asignatura]  
**Fecha:** [fecha de entrega]  
**Repositorio:** [enlace al repositorio de GitHub]

> Antes de exportar a PDF, reemplace todos los textos entre corchetes y agregue únicamente capturas reales de la práctica. El documento final debe tener un máximo de seis páginas.

## 1. Integrantes y roles

| Integrante | Rol en GitHub | Rol en Gitea |
| --- | --- | --- |
| Santiago Josué Márquez Carreño | [rol] | [responsabilidad] |
| [nombre 2] | [rol] | [responsabilidad] |
| [nombre 3] | [rol] | [responsabilidad] |
| [nombre 4] | [rol] | [responsabilidad] |

## 2. Trabajo colaborativo en GitHub

Creamos el repositorio `pagina-equipo-[N]` y protegimos `main` para exigir un Pull Request y una aprobación. Cada integrante desarrolló su perfil en una rama `feature/seccion-[nombre]`. Antes de integrar los cambios, otro compañero revisó el código, dejó un comentario y aprobó el PR.

**Captura A1 — Grafo de Git:**  
`[Insertar informe/capturas/01-grafo-git.png]`

**Captura A2 — PR con conflicto resuelto y comentario de revisión:**  
`[Insertar informe/capturas/02-conflicto-pr.png]`

### Resolución del conflicto

El conflicto ocurrió porque dos ramas nacieron desde la misma versión de `main` y cambiaron la misma línea del título en `index.html`. Después de fusionar la primera rama, Git ya no pudo decidir automáticamente qué título conservar en la segunda. Trajimos `main` a la rama pendiente, revisamos los marcadores de conflicto, acordamos el texto definitivo, eliminamos los marcadores y guardamos la solución en un nuevo commit.

## 3. Tailscale y Gitea

Tailscale creó una red privada entre las cuatro computadoras. Gracias a esa red, los integrantes pudieron abrir el Gitea alojado en la computadora del anfitrión mediante su IP `100.x.x.x`, sin abrir el puerto 3000 en el router ni publicar el servidor en Internet.

**Captura B — Cuatro equipos conectados en Tailscale y ping exitoso:**  
`[Insertar informe/capturas/03-tailscale.png]`

Al cerrar la terminal de Gitea, el proceso del servidor se detuvo y los demás equipos dejaron de acceder a la página y al remoto. Los compañeros usaron la IP de Tailscale porque `localhost` siempre se refiere a la misma computadora desde la que se escribe; en sus equipos, `localhost` no apunta a la laptop del anfitrión.

**Captura C/D — Gitea con historial y Pull Requests fusionados:**  
`[Insertar informe/capturas/04-gitea.png]`

Los commits creados durante la etapa de GitHub aparecieron en Gitea porque un `push` transfiere los objetos y referencias que forman la historia del repositorio. No fue necesario volver a crear los commits: Git conserva en cada copia su identificador, autor, fecha, mensaje y cambios.

## 4. Preguntas de comprensión

### 1. ¿Qué diferencia hay entre Git y GitHub? ¿Y entre GitHub y Gitea?

Git es el programa distribuido que registra versiones en cada computadora y permite crear ramas o commits incluso sin Internet. GitHub y Gitea alojan repositorios para compartirlos y ofrecen funciones como Issues y Pull Requests. GitHub funciona como un servicio administrado en la nube; Gitea se instala y administra en infraestructura propia, por lo que el equipo controla sus datos y también asume el mantenimiento.

### 2. ¿Para qué sirve una rama y por qué no trabajamos directo en `main`?

Una rama permite desarrollar un cambio sin alterar de inmediato la versión estable. En esta práctica cada perfil tuvo su propia rama, lo que permitió revisar los cambios y corregirlos antes de integrarlos. Evitar commits directos en `main` redujo el riesgo de publicar código incompleto y dejó evidencia de la revisión de cada compañero.

### 3. ¿Qué es un conflicto, por qué ocurrió y cómo se resolvió?

Un conflicto aparece cuando Git encuentra cambios incompatibles y necesita una decisión humana. Ocurrió al editar el mismo `<h1>` desde dos ramas creadas a partir del mismo estado. Actualizamos la segunda rama con `main`, elegimos en equipo el título definitivo, borramos los marcadores `<<<<<<<`, `=======` y `>>>>>>>`, y confirmamos la solución con un commit.

### 4. ¿Qué problema resolvió Tailscale?

Tailscale permitió que las cuatro laptops se comunicaran como si estuvieran en una red local privada aunque estuvieran en redes físicas distintas. Sin esta herramienta, desde casas diferentes no podríamos alcanzar directamente la IP local del anfitrión; habría que configurar el router, publicar un puerto o usar otro servidor accesible desde Internet, aumentando la complejidad y la exposición.

### 5. ¿Por qué pudimos hacer commits con Gitea apagado?

Git es distribuido: cada clon contiene el proyecto y su historia, y los commits se crean primero en el repositorio local. Gitea solo fue necesario para compartir los commits mediante `push` y recibir los de otros mediante `pull`. Cuando el servidor volvió a encenderse, pudimos enviar el trabajo acumulado sin perderlo.

### 6. ¿Cuándo conviene Gitea en lugar de GitHub?

Gitea conviene cuando una organización necesita mantener el código dentro de su propia red, aplicar políticas internas o trabajar con información que no debe alojarse en un servicio externo. Por ejemplo, una institución pública podría guardar en un Gitea interno el código de un sistema con integraciones sensibles. A cambio, debe encargarse de disponibilidad, actualizaciones, seguridad y respaldos.

## 5. Reflexión final

Alojar el código en la laptop de un compañero dio al equipo control directo, privacidad y un costo bajo. También introdujo riesgos: el servidor dejó de estar disponible cuando la laptop se apagó o perdió conexión, y una falla del disco podría afectar el repositorio si no existieran respaldos. GitHub ofrece mayor disponibilidad y mantenimiento administrado, mientras que Gitea permite decidir dónde se almacenan los datos. Para un uso real configuraríamos copias de seguridad y ejecutaríamos Gitea en un equipo dedicado.

## Lista de comprobación antes de entregar

- [ ] Nombres, número de equipo, asignatura, fecha y enlace completados.
- [ ] Cuatro PR de GitHub revisados y fusionados; cuatro Issues cerrados.
- [ ] Captura legible del grafo de Git.
- [ ] Captura del conflicto resuelto y del comentario de revisión.
- [ ] Captura de Tailscale con cuatro equipos y ping exitoso.
- [ ] Captura de Gitea con la historia y cuatro PR fusionados.
- [ ] Cada respuesta revisada por el integrante que la firma.
- [ ] PDF final de máximo seis páginas.

