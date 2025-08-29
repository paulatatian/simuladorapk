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

# Errores encontrados

### compatibilidad de versiones
```sh
Task :react-native-vision-camera:compileDebugKotlin FAILED
```
**Causa:** incompatibilidad entre **Gradle 8.x**, **Kotlin 2.2.0-RC** y **JDK 17**.

- **Solución:** instalar dependencia manualmente:
```bash
