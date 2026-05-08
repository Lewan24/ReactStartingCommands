# ReactStartingCommands
This is a simple set of common commands and things to do while creating a new react project.

## Set up default resolve of src dir
Add this to your <b>vite.config.ts</b><br>
```
resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
    },
  },
```

## Install common libraries
<li>Tailwind css</li>

```
npm install tailwindcss @tailwindcss/vite
```
Add below import to <b>vite.config.ts</b><br>
```
import tailwindcss from '@tailwindcss/vite'
```
And
```
tailwindcss()
```
to plugins.<br><br>

Import tailwind css to your .css file like <b>App.css</b><br>
```
@import "tailwindcss";
```

## Configure main files, router and default layout
<b><i>main.tsx</i></b>
```
import { createRoot } from "react-dom/client";
import App from "./app/App.tsx";
import "./styles/index.css";

createRoot(document.getElementById("root")!).render(<App />);
```
<b><i>index.css</i></b>
```
@import "tailwindcss";
```
<br>
<b><i>App.tsx</i></b>

```
import { RouterProvider } from 'react-router';
import { router } from './routes';

export default function App() {
  return <RouterProvider router={router} />;
}
```
<b><i>routes.tsx</i></b>
```
import { createBrowserRouter } from 'react-router';
import { Layout } from './components/layout/Layout';

//import { StartingPage } from './pages/StartingPage';
//import { ExamplePage } from './pages/ExamplePage';

export const router = createBrowserRouter([
  {
    path: '/',
    Component: Layout,
    children: [
      //{ index: true, Component: StartingPage },
      //{ path: 'example', Component: ExamplePage },
    ],
  },
]);
```
<b><i>Layout.tsx</i></b>
```
import { Outlet } from 'react-router';
import { Toaster } from 'sonner';

export function Layout() {
  return (
    <div className="flex min-h-screen bg-slate-50">
      <main className="flex-1 overflow-y-auto min-w-0">
        <Outlet />
      </main>
      <Toaster richColors position="top-right" />
    </div>
  );
}
```

## Common component and templates
If you need, you can use some of my common default ready to go components/templates like sidebar, apiClient or dockerfile<br>
They're stored in <b>Common</b> folder.

### Greetings
Thank you for checking out my github. Hope that this repo helps you faster start with next new project in react/vite.
