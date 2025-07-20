
# Proyecto VIRI

## Sistema de Ramas y Flujo de Trabajo

Este documento describe la estrategia de ramas Git para mantener un desarrollo ordenado, colaborativo y eficiente en el proyecto **VIRI**.

---

## 📂 Estructura de ramas

| Rama             | Uso principal                             | Usuarios                     |
|------------------|-----------------------------------------|-----------------------------|
| `main`           | Versión estable y lista para producción | Equipo de release y QA       |
| `dev`            | Rama de integración, versión en desarrollo | Todos los desarrolladores    |
| `feature/<nombre>` | Desarrollo de nuevas funcionalidades    | Cada desarrollador en su tarea |
| `hotfix/<nombre>`  | Correcciones urgentes en producción      | Equipo de mantenimiento      |
| `release/<versión>` | Preparación para release estable          | Equipo de release            |

---

## 🔄 Flujo de trabajo recomendado

### 1. Crear y trabajar en ramas feature

- Siempre parte de la rama `dev`:

```bash
git checkout dev
git pull origin dev
git checkout -b feature/tu-nombre-descriptivo
```

- Trabaja en tu rama `feature/<nombre>`, realiza commits claros y frecuentes.

### 2. Integrar cambios a `dev`

- Cuando termines tu feature, actualiza `dev` y haz merge:

```bash
git checkout dev
git pull origin dev
git merge feature/tu-nombre-descriptivo
git push origin dev
```

### 3. Correcciones urgentes con hotfix

- Para arreglos rápidos en producción, crea rama desde `main`:

```bash
git checkout main
git pull origin main
git checkout -b hotfix/arreglo-rapido
```

- Tras corregir, fusiona a `main` y `dev`:

```bash
git checkout main
git merge hotfix/arreglo-rapido
git push origin main

git checkout dev
git merge hotfix/arreglo-rapido
git push origin dev
```

### 4. Preparar una versión release

- Crea rama `release` desde `dev` para preparar release estable:

```bash
git checkout dev
git pull origin dev
git checkout -b release/vX.Y.Z
```

- Tras pruebas, fusiona a `main`, etiqueta la versión y sincroniza con `dev`:

```bash
git checkout main
git merge release/vX.Y.Z
git tag -a vX.Y.Z -m "Release versión X.Y.Z"
git push origin main --tags

git checkout dev
git merge release/vX.Y.Z
git push origin dev
```

---

## ✍️ Reglas y buenas prácticas

- **No trabajar directamente en `main` o `dev`.**
- Siempre crear ramas `feature/` para nuevas tareas con nombres claros.
- Hacer commits pequeños y frecuentes.
- Mantener `dev` actualizada antes de hacer merges.
- Usar Pull Requests para revisión de código antes de integrar cambios.

---

## 🛠 Ejemplo de nombres para ramas feature

| Rama                         | Descripción                    |
|------------------------------|-------------------------------|
| `feature/diego-login-ui`      | Desarrollo pantalla login      |
| `feature/diego-voice-control` | Funcionalidad control por voz |
| `feature/diego-bugfix-tracker`| Corrección en tracker          |

---

## Contacto

Para dudas o sugerencias, contacta a:  
**Diego Tercero** – [tu-email@example.com]

---

¡Gracias por colaborar para mantener el proyecto ordenado y profesional! 🚀
