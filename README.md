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

## Objetivo didáctico sugerido

Usar esta demo como portada de la clase y luego pedir a los estudiantes que:

1. Agreguen una nueva métrica al panel.
2. Modifiquen la agenda con su propio plan.
3. Construyan un nuevo bloque de UI reutilizable.
