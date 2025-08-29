This is a new [**React Native**](https://reactnative.dev) project, bootstrapped using [`@react-native-community/cli`](https://github.com/react-native-community/cli).

# Getting Started

> **Note**: Make sure you have completed the [Set Up Your Environment](https://reactnative.dev/docs/set-up-your-environment) guide before proceeding.

## Step 1: Start Metro

First, you will need to run **Metro**, the JavaScript build tool for React Native.

To start the Metro dev server, run the following command from the root of your React Native project:

```sh
# Using npm
npm start

# OR using Yarn
yarn start
```

## Step 2: Build and run your app

With Metro running, open a new terminal window/pane from the root of your React Native project, and use one of the following commands to build and run your Android or iOS app:

### Android

```sh
# Using npm
npm run android

# OR using Yarn
yarn android
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








