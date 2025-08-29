This is a new [**React Native**](https://reactnative.dev) project, bootstrapped using [`@react-native-community/cli`](https://github.com/react-native-community/cli).

# Proyecto: Aplicación Móvil con React Native

Este proyecto consiste en la creación de una aplicación móvil utilizando
**React Native**, con el objetivo de generar un archivo **APK** que
pueda instalarse en un emulador de Android para pruebas y validaciones.

## Requisitos Previos

Asegúrate de tener instaladas las siguientes herramientas en tu entorno
de desarrollo:

-   **Node.js** (versión recomendada: 20.x)
-   **npm** o **yarn** (gestores de dependencias)
-   **Java JDK** (versión 17.0.16)
-   **Gradle** (compatible con la versión instalada del JDK, en este
    caso 8.x)
-   **Android Studio** con las siguientes configuraciones:
    -   SDK Manager con la versión de Android necesaria.
    -   Emulador configurado para ejecutar la aplicación.
    -   Herramientas de compilación actualizadas.
-   **Kotlin** configurado en el proyecto (usando versión 1.8.22 o superior, según la compatibilidad de librerías).
## Instalación de Dependencias

Ejecuta el siguiente comando en la raíz del proyecto para instalar las
dependencias necesarias:

``` bash
npm install
```

# Dependencias clave instaladas manualmente:
```bash
npm install react-native-vision-camera
npm install react-native-reanimated@^3.10.0
npm install @react-native-camera-roll/camera-roll@^7.10.2
npm install react-native-worklets
```
Además, para poder usar los comandos de la CLI de React Native:
```bash
# agregar en package.json:
"devDependencies": {
  "@react-native-community/cli": "latest"
}

## Limpieza y Preparación del Proyecto

En caso de errores con Gradle o la compilación, es recomendable limpiar
la caché y reconstruir el proyecto:

``` bash
cd android
gradlew clean
cd ..
```
### Configuración de Permisos en Android
En el archivo android/app/src/main/AndroidManifest.xml, se añaden los permisos necesarios para acceder a la cámara y al almacenamiento:

```bash
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"
    android:maxSdkVersion="32" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
    android:maxSdkVersion="32" />
```

### Limpieza y Preparación del Proyecto

En caso de errores con Gradle o la compilación, es recomendable limpiar
la caché y reconstruir el proyecto:
```bash
cd android
gradlew clean
cd ..
```
También puede ser necesario limpiar cachés de Metro/React Native:
```bash
npx react-native start --reset-cache
```

### Construcción del APK
Para generar el APK de desarrollo, utiliza:
```bash
cd android
gradlew.bat assembleDebug
```
Para verificar revisa el archivo generado en:
```bash
android/app/build/outputs/apk/debug/app-debug.apk
```
### Ejecución en el Emulador
Para ejecutar la aplicación directamente en el emulador, utiliza:

```bash
npx react-native run-android
```

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Errores y Soluciones – Proyecto React Native + Android Emulator

Este documento recopila los principales errores, dependencias faltantes, conflictos de versiones y comandos utilizados durante la configuración y ejecución del proyecto en React Native con Android Studio Emulator.

# 1. Errores encontrados

### compatibilidad de versiones
```sh
Task :react-native-vision-camera:compileDebugKotlin FAILED
```
**Causa:** incompatibilidad entre **Gradle 8.x**, **Kotlin 2.2.0-RC** y **JDK 17**.

**Solución:** instalar dependencia manualmente:

```sh
npm i react-native-worklets
``` 

### Dependencia en Reanimated
```sh
throw new GradleException("[Reanimated] `react-native-worklets` library not found.
Please install it as a dependency in your project.
```
**Causa:** Dependencia faltante en Reanimated.

**Solución:** instalar dependencia manualmente:
```sh
npm i react-native-worklets
```

### CLI de React Native
```sh
react-native depends on @react-native-community/cli for cli commands.
```
**Causa:** CLI de React Native faltante.

**Solución:** instalar dependencia manualmente:
```sh
# agregar en package.json:
"devDependencies": {
  "@react-native-community/cli": "latest"
}
```
### Configuración de Permisos en Android
En el archivo android/app/src/main/AndroidManifest.xml, se añaden los permisos necesarios para acceder a la cámara y al almacenamiento:

```bash
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"
    android:maxSdkVersion="32" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
    android:maxSdkVersion="32" />
```

### Limpieza y Preparación del Proyecto

En caso de errores con Gradle o la compilación, es recomendable limpiar
la caché y reconstruir el proyecto:
```bash
cd android
gradlew clean
cd ..
```
También puede ser necesario limpiar cachés de Metro/React Native:
```bash
npx react-native start --reset-cache
```

### Construcción del APK
Para generar el APK de desarrollo, utiliza:
```bash
cd android
gradlew.bat assembleDebug
```
Para verificar, El archivo generado estará en:
```bash
android/app/build/outputs/apk/debug/app-debug.apk
```
### Ejecución en el Emulador
Para ejecutar la aplicación directamente en el emulador, utiliza:

```bash
npx react-native run-android
```







### SDK / NDK 
**Causa:** Varias versiones de NDK instaladas en:
```sh
C:\Users\ARROZPAISA\AppData\Local\Android\Sdk\ndk
```
- **Solución:** Configurar la versión fija en el proyecto.
```sh
# En el archivo android/build.gradle
ndkVersion = "27.1.12297006"
```

## 2. Cambios realizados en configuración/código

### Dependencias agregadas en `package.json`
- `@react-native-community/cli`
- `react-native-worklets`

### Compatibilidad de compilación
- Ajuste para trabajar con:
  - **JDK 17**
  - **Gradle 8.x**
  - **Kotlin 2.2.0-RC**

### Archivos revisados
- `AndroidManifest.xml` → Verificación y corrección de permisos y configuración del proyecto.
- `build.gradle` → Actualización de dependencias y versiones para asegurar compatibilidad con las librerías y herramientas utilizadas.

---
## 3. Versiones utilizadas

| Herramienta        | Versión detectada          |
|--------------------|----------------------------|
| **Java (JDK)**     | 17.0.16 (OpenJDK)          |
| **Gradle**         | 8.x                        |
| **Kotlin**         | 2.2.0-RC                   |
| **Android Emulator** | 36.1.9.0                  |
| **Node.js**        | 20.19.4                    |
| **React Native**   | 0.74.x (aprox.)            |








