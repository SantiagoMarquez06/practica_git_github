# Tareas de los integrantes para terminar la práctica

Este documento indica qué debe hacer cada integrante para completar la práctica y reunir las evidencias solicitadas. Los nombres se agregarán cuando el equipo los confirme.

## Paso inicial: aprobar la base del proyecto

El proyecto inicial está en el [Pull Request #2](https://github.com/SantiagoMarquez06/practica_git_github/pull/2). Antes de comenzar los perfiles:

1. Un integrante distinto al autor abre **Files changed**.
2. Deja al menos un comentario en una línea del código.
3. El autor responde al comentario y realiza una corrección si corresponde.
4. El revisor pulsa **Approve**.
5. El líder fusiona el PR con **Merge pull request**.
6. Todos clonan el repositorio o actualizan su rama `main`.

```powershell
git switch main
git pull origin main
```

## Integrante 1 — Líder e integrador

### En GitHub

- Invitar a los otros tres integrantes como colaboradores.
- Mantener protegida la rama `main` con una aprobación obligatoria.
- Crear cuatro Issues: uno para el perfil de cada integrante.
- Asignar cada Issue a su responsable.
- Completar `integrante-1.html` y su tarjeta en `index.html`.
- Trabajar desde una rama `feature/seccion-nombre`.
- Abrir su Pull Request y atender el comentario del revisor.
- Fusionar únicamente los Pull Requests revisados y aprobados.

### En Gitea

- Crear la organización `equipo-N`.
- Agregar a los cuatro integrantes con permiso de escritura.
- Crear el repositorio vacío del equipo.
- Agregar el remoto de Gitea y enviar la historia de `main`.

```powershell
git remote add gitea http://IP-TAILSCALE:3000/equipo-N/practica_git_github.git
git push gitea main
```

### Evidencia asignada

- Captura del resultado de:

```powershell
git log --oneline --graph --all
```

## Integrante 2 — Anfitrión del servidor

### En GitHub

- Completar `integrante-2.html` y su tarjeta en `index.html`.
- Trabajar desde su propia rama.
- Abrir un Pull Request y atender la revisión.

### En Tailscale

- Iniciar sesión y crear la tailnet del equipo.
- Invitar a los otros tres integrantes.
- Comprobar que aparezcan las cuatro computadoras.
- Compartir su IP de Tailscale con el equipo.
- Ejecutar un `tailscale ping` de prueba.

```powershell
tailscale status
tailscale ip -4
tailscale ping IP-DEL-ANFITRION
```

### En Gitea

- Instalar Gitea en su computadora.
- Ejecutar `gitea.exe web` y mantener abierta la terminal.
- Configurar SQLite como base de datos.
- Usar su IP de Tailscale como dominio y URL base.
- Comprobar que los demás puedan abrir `http://IP-TAILSCALE:3000`.

### Evidencia asignada

- Captura de Tailscale con las cuatro computadoras conectadas.
- Captura o terminal con un `tailscale ping` exitoso.

## Integrante 3 — Desarrollador y revisor

### En GitHub

- Completar `integrante-3.html` y su tarjeta en `index.html`.
- Trabajar desde su propia rama.
- Abrir un Pull Request y atender la revisión.
- Revisar el Pull Request asignado.

### Conflicto obligatorio

- Crear una rama desde `main` para cambiar el texto del `<h1>`.
- Coordinar con el integrante 4 para que ambos cambien la misma línea.
- Abrir su PR y fusionarlo primero.

### En Gitea

- Comprobar que aparezcan los commits realizados durante la etapa de GitHub.
- Revisar el gráfico de commits y la actividad de los integrantes.

### Evidencia asignada

- Captura de Gitea mostrando la historia importada desde GitHub.
- Captura del gráfico de commits de Gitea.

## Integrante 4 — Desarrollador y documentador

### En GitHub

- Completar `integrante-4.html` y su tarjeta en `index.html`.
- Trabajar desde su propia rama.
- Abrir un Pull Request y atender la revisión.
- Revisar el Pull Request asignado.

### Conflicto obligatorio

- Crear una rama desde el mismo estado de `main` que el integrante 3.
- Cambiar la misma línea del `<h1>` por un texto diferente.
- Después de fusionar el PR del integrante 3, actualizar su rama:

```powershell
git switch feature/titulo-4
git pull origin main
```

- Abrir `index.html`, elegir el título acordado y eliminar los marcadores `<<<<<<<`, `=======` y `>>>>>>>`.
- Confirmar y publicar la resolución:

```powershell
git add index.html
git commit -m "Resuelve conflicto en el título"
git push
```

### Documentación

- Reunir las capturas de los cuatro integrantes.
- Completar nombres, roles, asignatura, fecha y enlace en `informe/informe.html`.
- Sustituir los espacios de evidencia por capturas reales.
- Exportar el informe desde Chrome o Edge mediante **Imprimir → Guardar como PDF**.
- Verificar que el resultado tenga un máximo de seis páginas.

### Evidencia asignada

- Captura del Pull Request que muestre el conflicto resuelto.
- Captura del comentario de revisión.
- PDF final del informe.

## Cómo completar cada perfil

Cada integrante ejecuta:

```powershell
git switch main
git pull origin main
git switch -c feature/seccion-nombre
```

Después edita su archivo y su tarjeta en `index.html`:

| Integrante | Archivo |
| --- | --- |
| 1 | `integrante-1.html` |
| 2 | `integrante-2.html` |
| 3 | `integrante-3.html` |
| 4 | `integrante-4.html` |

Debe reemplazar **Nombre pendiente** y **Por definir** con:

- Nombre completo.
- Carrera.
- Hobby.
- Uno o dos proyectos favoritos.

Luego revisa y publica sus cambios:

```powershell
git status
git diff
git add index.html integrante-N.html
git commit -m "Agrega sección de Nombre"
git push -u origin feature/seccion-nombre
```

Finalmente abre un Pull Request, atiende el comentario del revisor y espera la aprobación antes del merge.

## Revisiones cruzadas

Cada revisor debe abrir **Files changed**, comentar una línea y aprobar después de que el autor atienda la observación.

| Pull Request | Revisor |
| --- | --- |
| Integrante 1 | Integrante 4 |
| Integrante 2 | Integrante 1 |
| Integrante 3 | Integrante 2 |
| Integrante 4 | Integrante 3 |

## Trabajo individual en Gitea

Después de importar el proyecto, el líder crea cuatro Issues para agregar proyectos favoritos. Cada integrante realiza el siguiente ciclo:

```powershell
git switch main
git pull gitea main
git switch -c feature/proyectos-nombre
# Editar integrante-N.html
git add integrante-N.html
git commit -m "Agrega proyectos favoritos de Nombre"
git push -u gitea feature/proyectos-nombre
```

Cada persona abre un Pull Request en Gitea. Otro integrante comenta y aprueba, y el líder lo fusiona.

## Lista final antes de entregar

- [ ] Los cuatro integrantes aparecen como colaboradores.
- [ ] La rama `main` está protegida.
- [ ] Los cuatro perfiles contienen datos reales.
- [ ] Cada integrante tiene commits propios.
- [ ] Hay al menos cuatro Pull Requests revisados y fusionados en GitHub.
- [ ] Los cuatro Issues de GitHub están cerrados.
- [ ] El conflicto fue provocado, resuelto y documentado.
- [ ] Tailscale muestra cuatro computadoras conectadas.
- [ ] Los cuatro integrantes pueden iniciar sesión en Gitea.
- [ ] Git muestra los remotos `origin` y `gitea`.
- [ ] La historia de GitHub aparece en Gitea.
- [ ] Hay cuatro Pull Requests revisados y fusionados en Gitea.
- [ ] El informe contiene nombres, enlace, respuestas y capturas reales.
- [ ] El PDF final tiene como máximo seis páginas.

