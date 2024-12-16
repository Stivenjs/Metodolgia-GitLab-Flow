# **Guía de la Metodología GitLab Flow**

## **¿Qué es GitLab Flow?**
GitLab Flow es una metodología de trabajo con Git que combina lo mejor de GitHub Flow y Git Flow, permitiendo una gestión eficiente de entornos de desarrollo, pruebas y producción. Su principal objetivo es facilitar la integración continua (CI) y el despliegue continuo (CD) en proyectos de desarrollo de software..

---

## **Ramas principales**
GitLab Flow se basa en tres ramas principales para controlar el flujo de trabajo:

1. **`main` (producción):**
   - Contiene la versión estable y lista para producción.
   - Solo se fusionan cambios que ya han sido probados.
   - Se usa para despliegues finales al entorno de producción.

2. **`staging` (preproducción):**
   - Actúa como un entorno intermedio para pruebas de integración y control de calidad.
   - Los desarrolladores fusionan sus cambios aquí antes de pasar a `main`.
   - Los testers y QA validan la funcionalidad en esta rama antes del despliegue final.

3. **`feature/*` (desarrollo de nuevas funcionalidades):**
   - Se crean ramas temporales desde `staging` para desarrollar nuevas funcionalidades o corregir errores.
   - Su formato suele ser `feature/nombre-de-la-funcion`.
   - Una vez finalizada la funcionalidad, se realiza un merge request (MR) para fusionarla con `staging`.

---

## **Flujo de Trabajo**
El flujo de trabajo se estructura de la siguiente manera:

1. **Crear una rama de funcionalidad (`feature/`)**
   - Los desarrolladores crean una rama `feature/nueva-funcionalidad` a partir de `staging`.
   - Se desarrolla la funcionalidad o corrección de errores en esta rama de forma aislada.

2. **Desarrollo y pruebas locales**
   - Se escriben códigos, pruebas unitarias y de integración.
   - Los cambios se confirman (commits) de forma regular para mantener un historial limpio.

3. **Merge Request (MR) hacia `staging`**
   - Cuando la funcionalidad está completa, se crea un Merge Request (MR) para fusionar la rama `feature/` en `staging`.
   - Otros desarrolladores y testers revisan el código antes de la fusión (revisión de código).

4. **Pruebas en `staging`**
   - Los cambios fusionados en `staging` se despliegan en un entorno de preproducción.
   - Se realizan pruebas automatizadas y manuales de control de calidad (QA).

5. **Fusión en `main` (producción)**
   - Una vez aprobados los cambios en `staging`, se fusionan en la rama `main`.
   - Los cambios pasan por un último ciclo de validación.
   - Los cambios se despliegan en el entorno de producción.

6. **Despliegue a producción**
   - La rama `main` se despliega al entorno de producción.
   - Los usuarios finales tienen acceso a la versión actualizada del software.

---

## **Comandos de Git recomendados**
A continuación, se muestran los comandos clave utilizados en cada etapa del flujo de trabajo.

**1. Crear una nueva rama de funcionalidad**
```bash
# Crear una rama de funcionalidad a partir de staging
git checkout staging
git checkout -b feature/nueva-funcionalidad
```

**2. Confirmar cambios y subirlos**
```bash
# Agregar archivos cambiados al commit
git add .

# Crear el commit con un mensaje descriptivo
git commit -m "Implementar nueva funcionalidad X"

# Subir la rama al repositorio remoto
git push origin feature/nueva-funcionalidad
```

**3. Crear una Pull Request en GitHub**
- Accede a GitHub y crea una Pull Reques (PR) desde la rama `feature/nueva-funcionalidad` hacia `staging`.
- Solicita revisión por parte de tus compañeros de equipo.

**4. Fusionar la rama en `staging`**
```bash
# Fusionar los cambios una vez aprobado el MR
git checkout staging
git merge feature/nueva-funcionalidad
```

**5. Fusionar `staging` con `main` para el despliegue**
```bash
# Fusionar staging con main cuando todo esté aprobado
git checkout main
git merge staging
```

**6. Eliminar la rama de funcionalidad**
```bash
# Eliminar la rama de funcionalidad una vez fusionada
git branch -d feature/nueva-funcionalidad
git push origin --delete feature/nueva-funcionalidad
```

---

## **Buenas prácticas**
Para que GitLab Flow funcione correctamente, se recomienda seguir estas prácticas:

- **Revisión de código:** Utilizar Pull Request para validar el código antes de fusionarlo con `staging` o `main`.
- **Commits claros y frecuentes:** Realizar commits con mensajes significativos y claros.
- **Estandarización de nombres de ramas:** Usar el formato `feature/nombre-descriptivo` para las ramas de funcionalidad.
- **Pruebas automatizadas:** Implementar pruebas automáticas para evitar errores en la fase de `staging`.
- **Revisiones de QA:** Realizar pruebas manuales y automáticas antes de fusionar con `main`.

---



