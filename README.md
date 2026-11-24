# 🌱 Brotito — app de hábitos (Proyecto SENA)

App móvil para crear hábitos, registrar actividades, configurar bloqueo de apps (modo enfoque)
y ver estadísticas. Cubre las 6 historias de usuario del documento (HU-RF01 a HU-RF06).
Los datos se guardan en el propio teléfono.

## Cómo sacar el APK

### Opción A — sin instalar nada (GitHub Actions)
1. Crea un repositorio en GitHub y sube **todo** el contenido de esta carpeta (incluida `.github`).
2. Ve a la pestaña **Actions** → **Construir APK de Brotito** → **Run workflow**
   (también se ejecuta solo en cada `push`). Tarda unos 5 minutos.
3. Entra a la ejecución terminada y descarga el artefacto **Brotito-APK** (un zip con `app-debug.apk`).
4. Pasa el `.apk` al celular, ábrelo y acepta *"Instalar apps de orígenes desconocidos"*.

### Opción B — con Android Studio
1. Instala Android Studio y ejecuta `npm install` en esta carpeta.
2. `npx cap sync android` y luego `npx cap open android`.
3. Menú **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
   El archivo queda en `android/app/build/outputs/apk/debug/app-debug.apk`.

## Probar rápido en el navegador (sin APK)
Abre `www/index.html` en Chrome. Para simular errores de las historias de usuario:
- `index.html?failsave=1` → falla al guardar (HU-RF04 criterio 4).
- `index.html?failstats=1` → falla al cargar estadísticas (HU-RF06 criterio 4).

## Cambios habituales
- Editas `www/index.html` → `npx cap sync android` → recompilas.
- Íconos: reemplaza los PNG de `assets/` y ejecuta `npm run icons`.

## Nota sobre el bloqueo de apps (HU-RF05)
Bloquear otras aplicaciones de verdad requiere permisos especiales de Android (Accesibilidad / uso de apps)
y código nativo. Esta versión implementa la configuración completa (crear, ver, modificar, evitar duplicados)
y un **modo enfoque** con cuenta regresiva. Es lo que se puede declarar como alcance del prototipo.
