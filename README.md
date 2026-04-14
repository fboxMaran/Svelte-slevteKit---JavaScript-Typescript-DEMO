# Demo de Clase: Svelte + SvelteKit (JS/TS)

Proyecto pensado para una clase de programación con una interfaz llamativa y dinámica:

- Hero visual moderno
- Métricas en vivo de participación y energía
- Comparativa rápida entre JavaScript y TypeScript
- Agenda de sesión lista para presentar

## Ejecutar en local

```sh
npm install
npm run dev -- --open
```

## Comandos útiles

```sh
# revisar tipos y componentes Svelte
npm run check

# compilar para producción
npm run build

# previsualizar build local
npm run preview
```

## Despliegue global con Vercel

Esta app ya está configurada con `@sveltejs/adapter-vercel`.

### Opción A: Desde la web de Vercel (recomendada)

1. Sube este proyecto a GitHub.
2. Entra a [Vercel](https://vercel.com/) y crea una cuenta (puede ser con GitHub).
3. Haz clic en **Add New Project** e importa tu repositorio.
4. Vercel detecta SvelteKit automáticamente.
5. Haz clic en **Deploy**.
6. Comparte la URL pública (por ejemplo: `https://tu-demo.vercel.app`).

### Opción B: Con CLI de Vercel

```sh
npm i -g vercel
vercel login
vercel
```

Para producción:

```sh
vercel --prod
```

Cada vez que hagas push a GitHub, Vercel puede desplegar cambios automáticamente.

## Cambiar entre LOCAL y GLOBAL (Vercel)

### 1) LOCAL (solo tu compu)

No necesitas cambiar código para usarla local. Siempre puedes correr:

```sh
npm install
npm run dev -- --open
```

Con eso la app vive en `http://localhost:5173`.

### 2) GLOBAL (internet) con Vercel

Pasos mínimos:

1. Confirma que el proyecto use `@sveltejs/adapter-vercel`.
2. Sube cambios a GitHub.
3. Importa el repo en Vercel y deploy.
4. Comparte tu URL pública (`https://tu-proyecto.vercel.app`).

### 3) Volver de GLOBAL a LOCAL

No hay que deshacer nada. Aunque esté configurada para Vercel, local funciona igual con:

```sh
npm run dev -- --open
```

### 4) Cambiar adapter (Vercel <-> Auto) en el futuro

Si un día quieres volver a `adapter-auto`:

```sh
npm install -D @sveltejs/adapter-auto
npm uninstall @sveltejs/adapter-vercel
```

Y en `svelte.config.js`:

```js
import adapter from '@sveltejs/adapter-auto';
```

Si luego quieres regresar a Vercel:

```sh
npm install -D @sveltejs/adapter-vercel
npm uninstall @sveltejs/adapter-auto
```

Y en `svelte.config.js`:

```js
import adapter from '@sveltejs/adapter-vercel';
```

### 5) Verificación rápida después de cualquier cambio

```sh
npm run check
npm run build
```

Si ambos comandos pasan, estás listo para local y para deploy.

## Objetivo didáctico sugerido

Usar esta demo como portada de la clase y luego pedir a los estudiantes que:

1. Agreguen una nueva métrica al panel.
2. Modifiquen la agenda con su propio plan.
3. Construyan un nuevo bloque de UI reutilizable.
