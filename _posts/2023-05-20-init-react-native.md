---
title: Init expo project with react native
tags: [react-native, expo]
---

## My work environment
- ubuntu
- nvm (0.39.0)
- node (v18.16.0)
- npm (9.5.1)
- yarn (1.22.19)

## References
[React Native document](https://reactnative.dev/docs/environment-setup)
[React Native paper document](https://callstack.github.io/react-native-paper/docs/guides/getting-started)
[Expo document](https://docs.expo.dev/get-started/create-a-project/)

## Steps
1. create expo-app
```sh
yarn create expo-app Yuniverse
```

2. Add dependency to enable tunnel
```sh
yarn add @expo/ngrok@^4.1.0
```

3. Start up expo
```sh
yarn expo start --tunnel
```

4. Add react-native-paper
```sh
yarn add react-native-paper react-native-safe-area-context
```