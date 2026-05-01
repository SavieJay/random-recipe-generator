# Random Recipe Generator

A modern, visually appealing web application that fetches and displays random recipes using Vue 3 and Vite.

## Project Overview

- **Core Technology:** [Vue 3](https://vuejs.org/) (Single File Components, Composition API with `<script setup>`).
- **Build Tool:** [Vite](https://vitejs.dev/).
- **API:** [TheMealDB](https://www.themealdb.com/api.php) for recipe data.
- **Styling:** Vanilla CSS with Custom Properties (Variables) for easy theming and responsive design.
- **Architecture:** Component-based UI with centralized state management in `App.vue`.

## Key Features

- **Random Recipe Discovery:** Fetch a new recipe with a single click.
- **Rich Recipe Details:** Includes title, category, origin (area), full ingredients list, step-by-step instructions, and YouTube links.
- **Dark Mode Support:** A built-in theme toggler that respects user preference and persists via the `data-theme` attribute.
- **Responsive Design:** Optimized for both desktop and mobile viewing.

## Development Commands

| Command | Description |
| :--- | :--- |
| `npm run dev` | Starts the Vite development server with Hot Module Replacement (HMR). |
| `npm run build` | Compiles and minifies the project for production into the `dist/` folder. |
| `npm run preview` | Locally previews the production build. |

## Development Conventions

- **Component Structure:** Store reusable UI elements in `src/components/`.
- **State Management:** For this small-scale app, state is managed using Vue `ref` and `onMounted` within `App.vue`.
- **Styling:**
    - Use CSS Variables (defined in `:root` and `[data-theme='dark']`) for all colors and transitions to maintain theme consistency.
    - Global styles are located in `src/style.css`.
- **API Integration:** API calls are performed using the native `fetch` API.

## File Structure

- `src/main.js`: Entry point of the application.
- `src/App.vue`: Main application component managing state and layout.
- `src/components/`:
    - `AppHeader.vue`: Header with the fetch action.
    - `RecipeCard.vue`: Displays the formatted recipe details.
    - `ThemeToggler.vue`: UI for switching between light and dark modes.
    - `LoadingState.vue` & `ErrorState.vue`: Conditional rendering components.
- `src/style.css`: Global styles and theme definitions.
