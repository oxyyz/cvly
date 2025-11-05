# CVLY

A modern Nuxt 4 application built with Vite, TypeScript, ESLint, Tailwind CSS, Pinia, and Docker.

## Tech Stack

- **Vite ⚡**: Fast build tool for web development
- **TypeScript 🛡️**: Type-safe code with TypeScript
- **ESLint & Stylistic 🧹**: Code quality and consistency with ESLint (Flat config) and Stylistic
- **Tailwind CSS 🌬️**: Utility-first CSS framework
- **Pinia 🍍**: State management for Vue & Nuxt
- **Docker 🐳**: Containerization for easy deployment and scalability
- **Custom Composables 🛠️**: API handling utilities like `useApi`

## Development Setup

### Prerequisites

- [Node.js](https://nodejs.org/) (v20 or higher, LTS `v22.21` recommended)
- [pnpm](https://pnpm.io/) (recommended) or [npm](https://www.npmjs.com/) / [Yarn](https://yarnpkg.com/)
- [Docker](https://www.docker.com/) (optional, for containerized development)

### Getting Started

1. Clone the repository:

```bash
git clone <repository-url>
cd cvly
```

2. Install dependencies:

```bash
pnpm install
```

3. Set up environment variables:

```bash
cp .env.example .env
# Edit .env with your configuration
```

4. Start the development server:

```bash
pnpm dev
```

5. Build for production:

```bash
pnpm build
```

## Project Structure

This project follows a flat structure suitable for Nuxt 4 applications. For larger projects, consider using [Nuxt layers](https://nuxt.com/docs/getting-started/layers).

```
cvly/
  ├── app/
  │    ├── assets/
  │    │    ├── css/
  │    │    ├── fonts/
  │    │    └── images/
  │    │
  │    ├── components/
  │    │    ├── Auth/
  │    │    │    ├── LoginForm.vue
  │    │    │    └── RegisterForm.vue
  │    │    └── User/
  │    │         └── ProfileCard.vue
  │    │
  │    ├── composables/
  │    │    ├── useApi.ts
  │    │    └── useApiFetch.ts
  │    │
  │    ├── constants/
  │    │    ├── maska.const.ts
  │    │    └── regexes.const.ts
  │    │
  │    ├── layouts/
  │    │    ├── default.vue
  │    │    └── auth.vue
  │    │
  │    ├── middleware/
  │    │    └── auth.global.ts
  │    │
  │    ├── pages/
  │    │    ├── index.vue
  │    │    ├── login.vue
  │    │    ├── register.vue
  │    │    └── profile.vue
  │    │
  │    ├── plugins/
  │    │    └── api.ts
  │    │
  │    ├── stores/
  │    │    ├── auth.store.ts
  │    │    └── user.store.ts
  │    │
  │    ├── types/
  │    │    ├── auth.types.ts
  │    │    ├── common.types.ts
  │    │    └── enums/
  │    │         ├── roles.enum.ts
  │    │         └── status.enum.ts
  │    │
  │    ├── utils/
  │    │    ├── sum.util.ts
  │    │    └── format-date.util.ts
  │    │
  │    ├── app.vue
  │    └── error.vue
  │
  ├── public/
  │    └── favicon.ico
  │
  ├── server/
  │    └── api/ (or any backend logic)
  │
  ├── nuxt.config.ts
  └── package.json
```

## Coding Conventions

### File Naming

- **Composables**: Must match composable function names (`useCamelCase.ts`)
- **Middlewares**: `kebab-case.ts`
- **Stores**: `kebab-case.store.ts` with store suffix
- **Types**: `kebab-case.types.ts` with types suffix
- **Enums**: Inside types directory, `kebab-case.enum.ts` with enum suffix
- **Components**: Directories and component names inside `components/` must be `Pascal/Case.vue`
- **Utilities**: `kebab-case.util.ts` with util suffix
- **Constants**: `kebab-case.const.ts` with const suffix & uppercase variable naming: `const RGX_PHONE = /^\d{10,15}$/`

### Vue Component Structure

Follow this structure for Vue components:

```vue
<script setup lang="ts">
interface Props {
  loading?: boolean; // Boolean props should be optional
}
const props = defineProps<Props>();

const emit = defineEmits<{
  submit: [data: Record<string, any>];
}>();

// Project provided first
const { $api } = useNuxtApp();
const route = useRoute();
const { t } = useI18n();
const localePath = useLocalePath();

// Custom composables
const api = useApi();

// Stores
const authStore = useAuthStore(); // Name just store if it's related to store like Login.vue

// Other stuff
const data = ref();

function sayHi() {
  console.log("HII");
}

const getData = computed(() => data.value);

watch(data, () => {
  console.log("Do something");
});
</script>

<template>...</template>

<style scoped>
...
</style>
```

## Code Quality

- Run ESLint before committing:

```bash
pnpm lint
```

- Fix ESLint issues automatically:

```bash
pnpm lint:fix
```

## Contributing

We welcome contributions! Please follow these guidelines:

### Getting Started

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes following our coding conventions
4. Ensure your code passes linting (`pnpm lint`)
5. Commit your changes (`git commit -m 'Add some amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Pull Request Guidelines

- Provide a clear description of what your PR does
- Reference any related issues
- Ensure all tests pass (if applicable)
- Ensure code passes linting
- Follow the project's coding conventions
- Keep PRs focused and reasonably sized

### Reporting Issues

- Use the issue tracker to report bugs or suggest features
- Provide clear steps to reproduce issues
- Include relevant environment information (Node.js version, OS, etc.)

## License

See [LICENSE](LICENSE) file for details.
