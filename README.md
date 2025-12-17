# Welcome to your Expo app 👋

This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
   npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.


<br/><br/><br/><br/>


# My Notes

## step 1 - Bootstraping the project


- Creating the project

```
npx create-expo-app@latest ./

npx expo start

npm run reset-project

npx expo start
```

- installing dependencies

```
npm install nativewind tailwindcss react-native-reanimated react-native-safe-area-context
```

- TailwindCss (Installation process) (visit [Nativewind](https://www.nativewind.dev/docs/getting-started/installation) for guidance)

<br/>

generating tailwindcss config file

```
npx tailwindcss init
```

<br/>

visit [Nativewind](https://www.nativewind.dev/docs/getting-started/installation) and change the contents of the config file

<br/>

tailwind.config.js

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  // NOTE: Update this to include the paths to all files that contain Nativewind classes.
  content: ["./App.tsx", "./app/**/*.{js,jsx,ts,tsx}", "./components/**/*.{js,jsx,ts,tsx}"],
  presets: [require("nativewind/preset")],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

<br/>

create app/global.css

<br/>

global.css

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

<br/>

create /babel.config.js (in root dir) and add the following from [Nativewind](https://www.nativewind.dev/docs/getting-started/installation)

```javascript
module.exports = function (api) {
  api.cache(true);
  return {
    presets: [
      ["babel-preset-expo", { jsxImportSource: "nativewind" }],
      "nativewind/babel",
    ],
  };
};
```
<br/>

Create a metro.config.js file in the root of your project if you don't already have one, then add the following configuration:

<br/>

creating metro.config.js

```
npx expo customize metro.config.js
```

<br/>

modifing the metro.config.js from [Nativewind](https://www.nativewind.dev/docs/getting-started/installation) (make sure input path is correct)

```javascript
const { getDefaultConfig } = require("expo/metro-config");
const { withNativeWind } = require('nativewind/metro');
 
const config = getDefaultConfig(__dirname)
 
module.exports = withNativeWind(config, { input: './app/global.css' })
```


<br/>

import your css file 

<br/>

./app/_layout.tsx

```typescript
import { Stack } from "expo-router";
import "./global.css";  // add this

export default function RootLayout() {
  return <Stack />;
}
```


<br/>

- Typescript setup (for nativewind/tailwindcss) mentioned in [Nativewind](https://www.nativewind.dev/docs/getting-started/installation)

<br/>

create /nativewind-env.d.ts (in root dir)

<br/>

nativewind-env.d.ts

```typescript
/// <reference types="nativewind/types" />
```


<br/><br/>

