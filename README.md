

---

````markdown
# 📱 Uni2 — Social Media Frontend

**Uni2** es una aplicación web tipo red social construida con **Vite**, **React** y autenticación mediante **Clerk**.  
Permite a los usuarios registrarse, iniciar sesión y acceder a la interfaz de la app.  
Todo el manejo de sesiones y autenticación se realiza a través de **Clerk**.

---

## 🚀 Tecnologías utilizadas

- [Vite](https://vitejs.dev/) — Bundler rápido para React.
- [React](https://react.dev/) — Librería principal para la UI.
- [Clerk](https://clerk.com/) — Autenticación de usuarios.
- [Tailwind CSS](https://tailwindcss.com/) — Estilos responsivos.

---

## 📦 Instalación

1. **Clonar el repositorio**

```bash
git clone https://github.com/tuusuario/uni2.git
cd uni2
````

2. **Instalar dependencias**

```bash
npm install
# o
yarn install
```

3. **Configurar Clerk**

* Crea una cuenta en [Clerk Dashboard](https://dashboard.clerk.com/).
* Crea una **nueva aplicación** en Clerk.
* Obtén tus llaves en la sección **API Keys**.

Crea un archivo `.env` en la raíz del proyecto con:

```env
VITE_CLERK_PUBLISHABLE_KEY=pk_test_*********************
```

⚠️ **Importante**:

* `VITE_CLERK_PUBLISHABLE_KEY` es pública y se usa en el navegador.
* En Vite, todas las variables que quieras usar en el frontend deben comenzar con `VITE_`.

4. **Ejecutar en desarrollo**

```bash
npm run dev
# o
yarn dev
```

La app estará disponible en:

```
http://localhost:5173
```

---

## 🛠 Configuración básica de Clerk en Vite + React

En `main.jsx`:

```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App.jsx';
import './index.css';
import { ClerkProvider } from '@clerk/clerk-react';

const clerkPubKey = import.meta.env.VITE_CLERK_PUBLISHABLE_KEY;

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <ClerkProvider publishableKey={clerkPubKey}>
      <App />
    </ClerkProvider>
  </React.StrictMode>,
);
```

---

## 🔒 Ejemplo de página protegida

```jsx
import { SignedIn, SignedOut, RedirectToSignIn } from '@clerk/clerk-react';

export default function Perfil() {
  return (
    <>
      <SignedIn>
        <h1>Bienvenido a tu perfil</h1>
      </SignedIn>
      <SignedOut>
        <RedirectToSignIn />
      </SignedOut>
    </>
  );
}
```

---

## 🌐 Despliegue en Vercel

1. Sube tu repo a GitHub.
2. Conéctalo a [Vercel](https://vercel.com/).
3. En **Project Settings → Environment Variables** añade:

```
VITE_CLERK_PUBLISHABLE_KEY=pk_test_*********************
```

⚠️ Clerk no permite usar el dominio `vercel.app` como producción.
Para producción, conecta un dominio propio en Vercel y configúralo en Clerk → **Paths & URLs** → **Application Domain**.

---

## 📌 Scripts disponibles

| Script    | Descripción                      |
| --------- | -------------------------------- |
| `dev`     | Inicia el servidor de desarrollo |
| `build`   | Genera la app para producción    |
| `preview` | Previsualiza la app en local     |

---

## 📄 Licencia

MIT License — Puedes usar y modificar libremente.

```

---

