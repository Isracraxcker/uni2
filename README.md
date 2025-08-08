# 📱 Uni2 — Social Media Frontend

**Uni2** es el frontend de una aplicación web de tipo red social construida con **React.js** y autenticación mediante **Clerk**.
Permite a los usuarios registrarse, iniciar sesión y acceder a la interfaz de la app.
Todo el manejo de sesiones y autenticación se realiza a través de **Clerk**.

---

## 🚀 Tecnologías utilizadas

* [Next.js](https://nextjs.org/) — Framework de React.
* [Clerk](https://clerk.com/) — Autenticación de usuarios.
* [Tailwind CSS](https://tailwindcss.com/) — Estilos responsivos.
* [React](https://react.dev/) — Librería principal para la UI.

---

## 📦 Instalación

1. **Clonar el repositorio**

```bash
git clone https://github.com/tuusuario/uni2.git
cd uni2
```

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
VITE_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_*********************

```

⚠️ **Importante**:

* `VITE_PUBLIC_CLERK_PUBLISHABLE_KEY` es pública y se usa en el navegador.


4. **Ejecutar en desarrollo**

```bash
npm run dev
# o
yarn dev
```

La app estará disponible en:

```
http://localhost:3000
```

---

## 🛠 Configuración básica de Clerk en Next.js

En `pages/_app.tsx` o `app/layout.tsx`:

```tsx
import { ClerkProvider } from '@clerk/nextjs';
import type { AppProps } from 'next/app';
import '../styles/globals.css';

export default function MyApp({ Component, pageProps }: AppProps) {
  return (
    <ClerkProvider {...pageProps}>
      <Component {...pageProps} />
    </ClerkProvider>
  );
}
```

---

## 🔒 Ejemplo de página protegida

```tsx
import { SignedIn, SignedOut, RedirectToSignIn } from '@clerk/nextjs';

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
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_*********************
CLERK_SECRET_KEY=sk_test_*********************
```

4. Haz el deploy.

---

## 📌 Scripts disponibles

| Script  | Descripción                      |
| ------- | -------------------------------- |
| `dev`   | Inicia el servidor de desarrollo |
| `build` | Genera la app para producción    |
| `start` | Inicia la app en producción      |

---

## 📄 Licencia

MIT License — Puedes usar y modificar libremente.

---

Si quieres, puedo incluir **capturas del dashboard de Clerk** directamente en este mismo README para que el desarrollador sepa dónde conseguir las llaves de entorno. Así sería 100% visual y fácil de seguir.
