# Guía de ejecución del equipo

Esta lista conserva la evidencia que pide la rúbrica. No fusionen ramas sin comentario y aprobación de otro integrante.

## 1. Datos que deben acordar

- Número del equipo.
- Nombre completo y usuario de GitHub de cada integrante.
- Quién será líder, anfitrión de Gitea, revisor y documentador.
- Qué carrera, hobby y emoji mostrará cada perfil.

## 2. Publicación inicial por el líder

La rama local `main` contiene el primer commit y `feature/base` contiene la estructura de la web. Después de crear en GitHub el repositorio `pagina-equipo-N`, el líder ejecuta:

```powershell
git remote add origin https://github.com/USUARIO-LIDER/pagina-equipo-N.git
git push -u origin main
git push -u origin feature/base
```

En GitHub debe crear el primer Pull Request de `feature/base` hacia `main`. Otro integrante comenta una línea, aprueba el PR y el líder lo fusiona. Después, todos clonan o actualizan `main`.

## 3. Perfil de cada integrante

Cada persona crea su rama desde `main` actualizado:

```powershell
git switch main
git pull origin main
git switch -c feature/seccion-nombre
```

Cada persona edita el archivo que corresponda a su número (`integrante-1.html`, `integrante-2.html`, `integrante-3.html` o `integrante-4.html`) y reemplaza el nombre, carrera, hobby y proyectos provisionales. También actualiza el nombre de su tarjeta dentro de `<ul id="integrantes">` en `index.html`. Las tarjetas ya están creadas con esta estructura:

```html
<li class="member-card">
  <a href="nombre.html">
    <span class="emoji" aria-hidden="true">🚀</span>
    <h3>Nombre del integrante</h3>
    <p>Ver perfil</p>
  </a>
</li>
```

Luego revisa y publica el cambio:

```powershell
git status
git diff
git add index.html integrante-N.html
git commit -m "Agrega sección de Nombre"
git push -u origin feature/seccion-nombre
```

Cada autor abre su PR. El revisor asignado deja al menos un comentario en `Files changed`; el autor responde con un nuevo commit y el revisor aprueba.

## 4. Conflicto obligatorio

Los integrantes 3 y 4 crean ramas desde el mismo `main` y cambian el texto del mismo `<h1>`. Después de fusionar la rama del integrante 3, el integrante 4 ejecuta:

```powershell
git switch feature/titulo-4
git pull origin main
```

Debe tomar una captura mientras `index.html` muestra los marcadores del conflicto. Luego acuerdan un título, eliminan los marcadores y ejecutan:

```powershell
git add index.html
git commit -m "Resuelve conflicto en el título"
git push
```

Antes de fusionar, deben capturar el PR con el comentario de revisión y la resolución registrada.

## 5. Captura del grafo

Cuando los cuatro PR estén fusionados:

```powershell
git switch main
git pull origin main
git log --oneline --graph --all
```

Guardar la captura como `informe/capturas/01-grafo-git.png`.

## 6. Tailscale y Gitea

El anfitrión inicia sesión en Tailscale e invita a los demás a su misma tailnet. Cuando los cuatro equipos aparezcan conectados, guarda la captura y un `tailscale ping` exitoso como `03-tailscale.png`.

Después de instalar Gitea, el anfitrión configura SQLite, usa su IP de Tailscale como dominio y crea la organización `equipo-N`. El repositorio de Gitea debe empezar vacío. El líder agrega el remoto y sube la historia:

```powershell
git remote add gitea http://IP-TAILSCALE:3000/equipo-N/pagina-equipo-N.git
git push gitea main
```

En Gitea deben proteger `main`, crear cuatro Issues y desarrollar cuatro ramas `feature/proyectos-nombre`, cada una mediante un PR revisado. La captura final debe mostrar los commits importados y los PR fusionados.

## 7. Informe

Completen `informe/informe.html`, reemplacen todos los corchetes e inserten las capturas reales. Ábranlo en Chrome o Edge, elijan **Imprimir → Guardar como PDF**, usen tamaño A4, escala 100 % y desactiven encabezados y pies de página. La plantilla genera seis páginas. `informe/INFORME.md` conserva el contenido en un formato cómodo para editar y revisar.
