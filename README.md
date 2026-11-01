# Vite React Boilerplate

![](/public/vite-react-boilerplate.png)

Everything you need to kick off your next Vite + React web app!

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Important Note](#important-note)
- [Testing](#testing)
- [Preparing for Deployment](#preparing-for-deployment)
- [DevTools](#devtools)
- [Installed Packages](#installed-packages)

## Overview

Built with type safety, scalability, and developer experience in mind. A batteries included Vite + React template.

- [pnpm](https://pnpm.io) - A strict and efficient alternative to npm with up to 3x faster performance
- [TypeScript](https://www.typescriptlang.org) - A typed superset of JavaScript designed with large scale applications in mind
- [ESLint](https://eslint.org) - Static code analysis to help find problems within a codebase
- [Prettier](https://prettier.io) - An opinionated code formatter
- [Vite](https://vitejs.dev) - Feature rich and highly optimized frontend tooling with TypeScript support out of the box
- [React](https://react.dev) - A modern front-end JavaScript library for building user interfaces based on components
- [Tailwind CSS](https://tailwindcss.com) - A utility-first CSS framework packed with classes to build any web design imaginable
- [Storybook](https://storybook.js.org) - A frontend workshop for building UI components and pages in isolation
- [TanStack Router](https://tanstack.com/router/v1) - Fully typesafe, modern and scalable routing for React applications
- [TanStack Query](https://tanstack.com/query/latest) - Declarative, always-up-to-date auto-managed queries and mutations
- [TanStack Table](https://tanstack.com/table/v8) - Headless UI for building powerful tables & datagrids
- [Zustand](https://zustand-demo.pmnd.rs) - An unopinionated, small, fast and scalable bearbones state-management solution
- [React Hook Form](https://react-hook-form.com) - Performant, flexible and extensible forms with easy-to-use validation
- [Zod](https://zod.dev) - TypeScript-first schema validation with static type inference
- [React Testing Library](https://testing-library.com) - A very light-weight, best practice first, solution for testing React components
- [Vitest](https://vitest.dev) - A blazing fast unit test framework powered by Vite
- [Playwright](https://playwright.dev) - Enables reliable end-to-end testing for modern web apps
- [Nivo](https://nivo.rocks) - A rich set of data visualization components, built on top of D3 and React
- [react-i18next](https://react.i18next.com/) - A powerful internationalization framework for React/React Native based on i18next
- [Faker](https://fakerjs.dev/) - Generate massive amounts of fake (but realistic) data for testing and development
- [Dayjs](https://day.js.org/en/) - A minimalist JavaScript library that parses, validates, manipulates, and displays dates and times for modern browsers
- [Husky](https://github.com/typicode/husky#readme) + [Commitizen](https://github.com/commitizen/cz-cli#readme) + [Commitlint](https://github.com/conventional-changelog/commitlint#readme) - Git hooks and commit linting to ensure use of descriptive and practical commit messages
- [ts-reset](https://github.com/total-typescript/ts-reset#readme) - Improvements for TypeScripts built-in typings for use in applications
- [Docker](https://www.docker.com) - Containerization tool for deploying your vite-react-boilerplate app

A more detailed list of the included packages can be found in the [Installed Packages](#installed-packages) section. Packages not shown above include Devtools, ui helper libraries, and eslint plugins/configs.

## Requirements

- [NodeJS 24+](https://nodejs.org/en)
- [pnpm](https://pnpm.io) (or equivalent)

If you'd like to use the included Dockerfile then [Docker](https://www.docker.com) is required as well:

## Getting Started

Getting started is a simple as cloning the repository

```
git clone git@github.com:RicardoValdovinos/vite-react-boilerplate.git
```

Changing into the new directory

```
cd vite-react-boilerplate
```

Removing the .git folder (and any additional files, folders or dependencies you may not need)

```
rm -rf .git
```

Installing dependencies

```
pnpm install
```

And running the setup script (initializes git repository and husky and installs playwright)

```
pnpm run setup
```

Congrats! You're ready to starting working on that new project!

If you'd rather run the commands above in one go, check out the command below:

```
git clone git@github.com:RicardoValdovinos/vite-react-boilerplate.git &&\
cd vite-react-boilerplate &&\
rm -rf .git &&\
pnpm install &&\
pnpm run setup
```

**Note**: This project comes with two git hooks added by [husky](https://typicode.github.io/husky/). A prepare-commit-msg hook to run the [Commitizen](https://github.com/commitizen/cz-cli#readme) cli for those nice commit messages and a commit-msg hook to run [Commitlint](https://commitlint.js.org/#/) on the message itself. Commitlint will ensure the commit message follows the [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/) (it will if you used commitizen).

If you wish to remove any hooks, simply delete the corresponding file in the .husky directory.

## Important Note

1. This boilerplate project does not include a demo. At most, a few utilities (types, devtools, initial home page routes) are included. There is no glue to get in your way when trying to modify the template.

2. Due to empty directories not being included in git commits, placeholder README files have been added to these empty directories. These README files contain simple descriptions about how the different directories in the accompanying folder structure may be used. As an example check out the [recommended component organizational structure](src/components/README.md) as well as the [recommended folder structure](src/features/README.md).

3. [Faker](https://fakerjs.dev/) is included to encourage more isolated testing and allow for rapid development of demos and MVPs. However, please make note that, [due to a bug](https://github.com/faker-js/faker/issues/1791), importing Faker from the main package (without a locale) will result in the entire Faker lib being imported causing bundle sizes to increase up to 2+ MB. Instead prefer [localized imports](https://fakerjs.dev/guide/localization.html#individual-localized-packages) as shown below.

   ```
   // import { faker } from '@faker-js/faker';
   import { faker } from '@faker-js/faker/locale/en'; // prefer localization when possible
   ```

   The imported lib will instead be around 600 KB. Nonetheless, Faker should **NOT** be used in production and instead be limited to testing and demos.

4. Starting May 2025, this project and its dependencies are set to be updated once a month or as issues/PR's come in.

## Testing

Unit testing is handled by React Testing Library and Vitest while End-to-End (E2E) Testing is conducted by Playwright.

If you'd like to run all tests, Unit and E2E alike, execute the following command:

```
pnpm run test
```

### Unit Testing

When running unit test scripts, it is assumed that unit tests will be colocated with the source files. Take a look at the placeholder README file in `src/components` for [an example](src/components/README.md).

If you'd like to execute unit tests specifically, the below command will execute vitest:

```
pnpm run test:unit
```

If instead you are interested in coverage reporting, run:

```
pnpm run test:unit:coverage
```

All unit tests run in watch mode by default. If you'd like to disable watch mode, change the package.json test scripts with the following

before:

```
"scripts": {
  	"test:unit": "vitest src/",
	"test:unit:coverage": "vitest --coverage src/"
}
```

After:

```
"scripts": {
  	"test:unit": "vitest run src/",
	"test:unit:coverage": "vitest run --coverage src/"
}
```

**Note**: Faker is included to provide mock data. See the [Important Note](#important-note) section for crucial details regarding this package. Specifically, point 3.

### End-to-End (E2E) Testing

Running E2E tests use a similar syntax to running unit tests:

```
pnpm run test:e2e
```

If you wish to see the reports, run:

```
pnpm run test:e2e:report
```

## Preparing for Deployment

Instructions are provided for deploying both with and without Docker. Both options still require a platform to host the application.

### Without Docker

Deploying is as easy as running

```
pnpm run build
```

and pointing your web server to the generated `index.html` file found at `dist/index.html`

### With Docker

A Dockerfile with an [NGINX](https://www.nginx.com) base image is also provided for quick and easy deployments. Simply execute the following commands:

1. `pnpm run build`
2. `docker build . -t <container_name>`
   - Example: `docker build . -t todo-app`
3. `docker run  -p <port_number>:80 <container_name>`
   - Example: `docker run -p 8080:80 todo-app`

### Continuous Integration

Due to the vast array of tools, opinions, requirements and preferences a CI template is not included in this project.

## Devtools

This project includes a set of Devtools. Some are additional package dependencies whereas others come built-in to the packages themselves.

### Devtool dependencies:

- [@tanstack/react-query-devtools](https://tanstack.com/query/v4/docs/react/devtools) - Dedicated dev tools to help visualize the inner workings of React Query
- [@tanstack/router-devtools](https://tanstack.com/router/v1/docs/devtools) - Dedicated dev tools to help visualize the inner workings of TanStack Router
- [@tanstack/react-table-devtools](https://www.npmjs.com/package/@tanstack/react-table-devtools) - Dedicated dev tools to help visualize the inner workings of TanStack Table
- [@hookform/DevTools](https://react-hook-form.com/dev-tools) - React Hook Form Devtools to help debug forms with validation

A set of utility components are provided in `src/components/utils/development-tools/`. These [wrapper components](https://tanstack.com/router/v1/docs/devtools#only-importing-and-using-devtools-in-developmentgit) check whether the application is running in development or production mode and render the component or null respectively. In other words, you can confidently use them during development without having to worry about them showing up for end users in production.

**TanStack Query Devtools** are ready to go out of the box. The development vs. production rendering mechanism is built into the devtools. If you do wish to [render the devtools in production](https://tanstack.com/query/latest/docs/react/devtools) you can freely do so by following the TanStack Query Devtools documentation. The devtools component can be found in `src/App.tsx`.

When running the application in development mode you can find the TanStack Query Devtools icon in the bottom left corner of the page sporting the [React Query Logo](https://img.stackshare.io/service/25599/default_c6db7125f2c663e452ba211df91b2ced3bb7f0ff.png).

**TanStack Router Devtools**, however, utilizes its respective utility component in this project. The initial setup has been taken care of but if you wish to modify or remove the component, have a look in `src/App.tsx`.

The TanStack Router Devtools icon can be found in the bottom right corner of the page denoted by the vertically stacked "TANSTACK ROUTER" logo.

The above components, along with their imports, are commented out to start.

**TanStack Table Devtools** Documentation is, at the time of writing this, non-existent. Having said that, usage is similar to the other TanStack devtools. A utility component restricting the devtools to development builds has been provided. The difference in comparison to the other TanStack devtools is the lack of floating mode. Instead, the Devtools are rendered as a component within the actual TanStack Table you define. An additional caveat being that the DevTools component (built-in and provided utility alike) require a table prop from the `useReactTable()` hook. In other words, if you have multiple tables, each table must have its own Devtools component. Check the simplified code below.

```
function Table(): FunctionComponent {
  /* some code */

  const table = useReactTable({
    data,
    columns,
    getCoreRowModel: getCoreRowModel(),
  });

  return (
    <>
      {/* table code */}
      <TanStackTableDevelopmentTools table={table} />
    </>
  )
}
```

**React Hook Form DevTools** icon can be recognized in the top right corner of the page by the pink React Hook Form clipboard logo. A utility component has also provided. Like the TanStack Table Devtools component above, a prop must be passed from a specific hook. In this case, it is the control prop from the `useForm()` hook. Similar to TanStack Table, use of React Hook Form DevTools requires the component be added to each unique form. More information can be found in the [React Hook Form DevTools documentation](https://react-hook-form.com/dev-tools).

To reiterate, if you wish to restrict the Devtools to development builds use the provided components found at `src/components/utils/development-tools` instead of the built-in components from their respective modules.

### Built-in Devtools:

- Zustand

**Zustand** provides a built-in [devtools middleware](https://github.com/pmndrs/zustand#redux-devtools) for use with [Redux DevTools](https://github.com/reduxjs/redux-devtools#redux-devtools).

## Installed Packages

A simplified list can be found in the [Overview](#overview) section.

### Base

- [TypeScript](https://www.typescriptlang.org)
- [Vite](https://vitejs.dev)
- [React](https://react.dev)

### Routing

- [TanStack Router](https://tanstack.com/router/v1)

### Linting & Formatting

- [ESLint](https://eslint.org)
  - [typescript-eslint](https://typescript-eslint.io)
  - [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier#readme)
  - [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react#readme)
  - [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks)
  - [eslint-plugin-react-refresh](https://github.com/ArnaudBarre/eslint-plugin-react-refresh)
  - [eslint-plugin-unicorn](https://github.com/sindresorhus/eslint-plugin-unicorn#readme)
  - [eslint-plugin-storybook](https://github.com/storybookjs/eslint-plugin-storybook#readme)
- [Prettier](https://prettier.io)

### State Management

- [TanStack Query (React Query)](https://tanstack.com/query/latest)
- [Zustand](https://zustand-demo.pmnd.rs)

### UI

- [Tailwind CSS](https://tailwindcss.com)
- [HeadlessUI](https://headlessui.com)
- [heroicons](https://heroicons.com)
- [TanStack Table](https://tanstack.com/table/v8)
- [Storybook](https://storybook.js.org)

### Forms

- [React Hook Form](https://react-hook-form.com)
- [Zod](https://zod.dev)

### Data Visualization

- [Nivo](https://nivo.rocks)
  - [Line](https://nivo.rocks/line/)
  - [Bar](https://nivo.rocks/bar/)
  - [Pie](https://nivo.rocks/pie/)

### Testing

- [Vitest](https://vitest.dev)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Playwright](https://playwright.dev)

### Development Tools

- [TanStack Query Devtools](https://tanstack.com/query/latest/docs/react/devtools?from=reactQueryV3&original=https%3A%2F%2Ftanstack.com%2Fquery%2Fv3%2Fdocs%2Fdevtools)
- [TanStack Router Devtools](https://tanstack.com/router/v1/docs/devtools)
- [TanStack Table Devtools](https://www.npmjs.com/package/@tanstack/react-table-devtools)
- [React Hook Form Devtools](https://react-hook-form.com/dev-tools)

### Git

- [Husky](https://github.com/typicode/husky#readme)
- [Commitizen](https://github.com/commitizen/cz-cli#readme)
- [Commitlint](https://github.com/conventional-changelog/commitlint#readme)

### Other

- [i18next-browser-languageDetector](https://github.com/i18next/i18next-browser-languageDetector)
- [i18next](https://www.i18next.com/)
- [react-i18next](https://react.i18next.com/)
- [ts-reset](https://github.com/total-typescript/ts-reset#readme)
- [Faker](https://fakerjs.dev/)
- [Dayjs](https://day.js.org/en/)

---

# Лабораторна робота №7 — Дослідження бойлерплейту фронтенд-додатку

**Мета:** проаналізувати готовий template-проєкт (Vite + React + TypeScript), розібрати його
конфігураційні файли та точку входу, навчитись швидко орієнтуватись у чужому фронтенд-проєкті та
переконатися у роботі Hot Module Replacement (HMR).

**Проєкт:** <https://github.com/RicardoValdovinos/vite-react-boilerplate> (клон у `F:\practis\kpz7`,
коміт `e086793`).

---

## Етап 1. Запуск бойлерплейту

Послідовність, виконана на Windows (Git Bash):

| Крок | Команда | Результат |
| --- | --- | --- |
| Клонування | `git clone https://github.com/RicardoValdovinos/vite-react-boilerplate F:/practis/kpz7` | робоче дерево гілки `main` на коміті `e086793` |
| Встановлення залежностей | `pnpm install` | `node_modules` з `pnpm-lock.yaml` без змін |
| Підготовка | `pnpm run setup` | `husky init`, `playwright install`, видалення `.husky/pre-commit` (`git init` на вже клонованому репозиторії нічого не псує) |
| DEV-сервер | `pnpm run dev` | `VITE v8.0.16 ready in 1513 ms` → `http://localhost:5173/` |
| DEV-сервер (команда з методички) | `npm run dev` | те саме: `VITE v8.0.16 ready in 1374 ms` → `http://localhost:5173/` |

Скріншот стартової сторінки: `docs/screenshots/7-01-dev-server-start.png`.

> **Важливо.** Перший запуск дав помилки в консолі браузера та HTTP 500 на модулях
> `/src/common/i18n.ts` і `/src/components/utils/development-tools/TanStackRouterDevelopmentTools.tsx`.
> Методичка вимагає «стартову сторінку додатку без помилок у консолі», тому причину було знайдено і
> усунено — див. розділ «Знайдена вада бойлерплейту».

Після виправлення:

- `npx tsc --noEmit` — вихід 0;
- `pnpm lint` (`eslint --max-warnings 0`) — вихід 0;
- консоль браузера — без помилок, залишились лише попередження (див. «Спостереження консолі»).

---

## Етап 2. Аналіз структури

### 2.1. Ключові директорії

```
kpz7/
├── index.html                  # HTML-шаблон: <div id="root"> + <script type="module" src="/src/main.tsx">
├── vite.config.ts              # конфіг Vite: плаґіни, server, test
├── tsconfig.json               # строга конфігурація TypeScript, "noEmit": true
├── tsconfig.node.json          # типізація для самого vite.config.ts
├── prettier.config.js          # табуляція, подвійні лапки, printWidth 80, endOfLine lf
├── eslint.config.js            # flat config: JS/TS/React/a11y/unicorn + prettier
├── commitlint.config.cjs       # conventional commits
├── playwright.config.ts        # e2e-тести (webServer автозапускає dev-сервер)
├── vitest.setup.ts             # розширення expect засобами @testing-library/jest-dom
├── tailwind.config.js          # залишок від Tailwind v3, див. п. 2.6
├── .env                        # VITE_APP_ENVIRONMENT="development"
├── e2e/                        # Playwright-спеки
├── public/                     # статика, яка копіюється в dist як є
└── src/
    ├── main.tsx                # точка входу
    ├── App.tsx                 # провайдери (React Query, Router) + devtools
    ├── routeTree.gen.ts        # АВТОГЕНЕРОВАНИЙ файл, не редагувати вручну
    ├── routes/                 # file-based routing
    ├── pages/                  # сторінки (Home)
    ├── components/             # UI, форми, графіки, development-tools
    ├── common/                 # i18n.ts, types.ts, utilities.ts
    ├── assets/locales/         # {en,es}/translations.json
    ├── styles/tailwind.css     # @import "tailwindcss";
    └── store/ hooks/ features/ # порожні директорії-заготовки (лише README.md)
```

Шаблон орієнтований на feature-based архітектуру: `pages` — сторінки під маршрути, `components` —
перевикористовуване UI, `features`/`hooks`/`store` — заготовки під бізнес-логіку, локальний і
глобальний стан (Zustand).

### 2.2. `package.json`

`"type": "module"` — проєкт ESM, тому всі конфіги записані як `export default`.

**dependencies** (19 пакетів — те, що потрапляє у браузер):

| Група | Пакети |
| --- | --- |
| UI-ядро | `react@19.2.7`, `react-dom@19.2.7` |
| Маршрутизація і дані | `@tanstack/react-router@1.170.16`, `@tanstack/react-query@5.101.0`, `@tanstack/react-table@8.21.3` |
| Стан | `zustand@5.0.14` |
| Форми і валідація | `react-hook-form@7.80.0`, `@hookform/resolvers@5.4.0`, `zod@4.4.3` |
| Локалізація | `i18next@26.3.1`, `react-i18next@17.0.8`, `i18next-http-backend@4.0.0`, `i18next-browser-languagedetector@8.2.1` |
| Графіки | `@nivo/core`, `@nivo/bar`, `@nivo/line`, `@nivo/pie` (0.99.0) |
| Дати | `dayjs@1.11.21` |
| Сторожовий випадок | `@storybook/addon-docs` лежить у **dependencies**, а не в devDependencies |

**devDependencies** (45 пакетів) за групами:

| Група | Пакети |
| --- | --- |
| Збірка і dev-сервер | `vite@8.0.16` (rolldown-збірка), `@vitejs/plugin-react-swc@4.3.1` |
| Плаґіни для Vite | `@tailwindcss/vite`, `@tanstack/router-plugin`, `rollup-plugin-copy` |
| TypeScript | `typescript@6.0.3`, `@types/node`, `@types/react`, `@types/react-dom`, `@total-typescript/ts-reset` |
| Якість коду | `eslint@9.39.4` + 8 плагінів (`react`, `react-hooks`, `import`, `jsx-a11y`, `unicorn`, `react-refresh`, `storybook`, `eslint-config-prettier`), `typescript-eslint`/`@typescript-eslint/*`, `prettier@3.8.4`, `globals` |
| Тестування | `vitest@4.1.9`, `@vitest/coverage-v8`, `@testing-library/{react,jest-dom,user-event}`, `jsdom`, `@playwright/test@1.61.0`, `@faker-js/faker` |
| Допоміжники UI | `@headlessui/react`, `@heroicons/react`, `prop-types` |
| Devtools | `@tanstack/{react-query-devtools,react-table-devtools,router-devtools}`, `@hookform/devtools` |
| Storybook | `storybook@10.4.6`, `@storybook/react-vite`, `@storybook/addon-{links,themes}` |
| Git-процес | `husky@9.1.7`, `commitizen`, `cz-conventional-changelog`, `@commitlint/{cli,config-conventional}` |
| Утиліти скриптів | `shx` (кросплатформенний `rm` у скриптах), `tailwindcss@4.3.1`, `autoprefixer` |

**scripts** — що фактично виконується:

| Скрипт | Команда | Призначення |
| --- | --- | --- |
| `setup` | `git init && npx husky init && npx playwright install && shx rm .husky/pre-commit` | одноразова ініціалізація після клонування; `shx` замість `rm`, щоб команда працювала і на Windows |
| `dev` | `vite` | dev-сервер з HMR на порті 5173 |
| `build` | `tsc && vite build` | спершу перевірка типів, потім продакшн-збірка: помилка типів зупиняє білд |
| `preview` | `vite preview` | локальний перегляд зібраного `dist/` |
| `lint` / `lint:fix` | `eslint --max-warnings 0` | нульова толерантність до попереджень |
| `format` | `prettier "src/**/*.{ts,tsx}" --write` | стилі коду |
| `test` | `vitest run src/ && playwright test` | юніт + e2e разом |
| `test:unit` / `test:unit:coverage` | `vitest src/` / `vitest --coverage src/` | лише юніт-тести |
| `test:e2e` / `test:e2e:report` | `playwright test` / `playwright show-report` | лише e2e |
| `storybook` / `storybook:build` | `storybook dev -p 6006` / `storybook build` | workshop для компонентів |
| `prepare` | `husky` | установлює git-хуки, спрацьовує автоматично після `pnpm install` |
| `commitlint` / `commitizen` | `commitlint --edit` / `git cz` | валідація та інтерактивний формат коміту |

### 2.3. `vite.config.ts`

Файл на 33 рядки, чотири плаґіни (порядок значущий):

```ts
plugins: [
  react(),          // @vitejs/plugin-react-swc — транспіляція через SWC + Fast Refresh
  tailwindcss(),    // @tailwindcss/vite — Tailwind v4 обробляється всередині Vite, без PostCSS
  tanstackRouter(), // @tanstack/router-plugin — генерує src/routeTree.gen.ts за файлами з src/routes
  copy({ targets: [{ src: "./src/assets/locales", dest: "./public" }] }), // rollup-plugin-copy
]
```

- **Шляхи (аліаси).** У конфігу **немає** секції `resolve.alias`. Увесь проєкт імпортує відносними
  шляхами (`./utilities`, `../../../common/utilities`). Модуль `node:path` використаний лише для
  `path.resolve()` і `normalizePath()` у цілях плаґіна `copy`: `rollup-plugin-copy` не приймає
  Windows-шляхи з зворотною похилкою, а `normalizePath` перетворює їх на `/`.
- `server: { host: true, strictPort: true }` — сервер слухає усі мережеві інтерфейси (доступний з
  локальної мережі чи мобільного пристрою) і **не** перемикається на інший порт: якщо 5173 зайнятий,
 запуск упаде з помилкою замість тихо взяти 5174.
- `test: { environment: "jsdom", setupFiles: ["./vitest.setup.ts"], css: true }` — конфіг Vitest живе
  у тому ж файлі, саме тому `defineConfig` імпортується з `vitest/config`, а не з `vite`.
- Плаґін `copy` — компроміс шаблону: i18next у продакшні завантажує переклади з
  `locales/{{lng}}/translations.json`, тому під час збірки директорію `src/assets/locales` копіюють у
  `public/`, з якої Vite забирає статичні файли в `dist/`.

### 2.4. `src/main.tsx` — точка входу

Ланцюжок: `index.html` → `/src/main.tsx` → `createRouter({ routeTree })` →
`ReactDOM.createRoot(...).render(...)`.

- `import "./styles/tailwind.css"` і `import "./common/i18n"` — побічні ефекти, які роблять стилі та
  `t()` доступними в будь-якому компоненті без додаткових імпортів.
- `routeTree` імпортується з **автогенерованого** `src/routeTree.gen.ts`.
- `declare module "@tanstack/react-router" { interface Register { router: TanstackRouter } }` —
  реєстрація типу маршрутизатора: саме це дає виведену типізацію `useNavigate()`, `<Link to="...">` і
  параметрів маршрутів.
- `ReactDOM.createRoot(document.querySelector("#root"))` обгорнуто в `if (!rootElement.innerHTML)` —
  захист від повторного монтування.
- Дерево рендеру: `React.StrictMode` → `React.Suspense fallback="loading"` → `<App router={router} />`;
  `App.tsx` додає `QueryClientProvider`, `RouterProvider` і devtools (Router + React Query), які
  зникають у продакшні завдяки `isProduction`-перевірці в `src/components/utils/development-tools/*`.

### 2.5. `src/routes/` — file-based routing і зв'язок шляху з компонентом

```ts
// src/routes/index.ts
export const Route = createFileRoute("/")({ component: Home });

// src/routes/__root.ts
export const Route = createRootRoute(); // без component → <Outlet/> по замовчуванню
```

- Шлях `/` прив'язаний до `Home` саме тут. Плаґін `tanstackRouter()` сканує `src/routes` і на кожен
  файл створює запис у `src/routeTree.gen.ts` (у згенерованому коді видно ланцюжок
  `createFileRoute("/")` → `rootRoute.addChildren([...])`).
- Новий шлях = новий файл: `src/routes/about.ts` із `createFileRoute("/about")` дає `/about` без
  ручного реєстрування. Тому `routeTree.gen.ts` не редагують — наступна генерація перезапише файл.
- Одразу після генерації `routeTree.gen.ts` має форматування плагіна; `pnpm format` приводить його до
  prettier-стилю проєкту (у нашій роботі саме тому файл опинився в дифі).

### 2.6. `src/pages/Home.tsx` і стилі

`Home` — демонстраційний компонент: `useTranslation()` дає `t("home.greeting")` («Hello, world!» із
`src/assets/locales/en/translations.json`), кнопка `translate` перемикає мову
`i18n.changeLanguage("en" ↔ "es")`. Уся візуалізація — tailwind-класи
(`bg-blue-300 w-screen h-screen flex flex-col justify-center items-center text-6xl`), окремого CSS-файлу
під компонент немає.

Імпортів **інших компонентів у `Home.tsx` немає**: рядок `import { useTranslation } from "react-i18next"`
і `import type { FunctionComponent } from "../common/types"` — єдині два. `FunctionComponent` тут — це
не тип функції, а аліас `React.ReactElement | null` (див. `src/common/types.ts`), тож сигнатура
`export const Home = (): FunctionComponent => …` означає «компонент повертає елемент або null». Уся
конвенція проєкту побудована на цьому: кожен компонент і `App.tsx`, і devtools-обгортки мають однакову
сигнатуру, тому легко замінюються та обертаються в `React.lazy`. Справжні «інші компоненти» живуть у
`src/components/` (devtools, графіки Nivo, форми), але в `Home` не підключені — доки реальний застосунок
не почне їх використовувати.

`src/styles/tailwind.css` — один рядок `@import "tailwindcss";`. Це Tailwind **v4**: конфігурація живе в
CSS (`@theme`), а плаґін `@tailwindcss/vite` збирає утиліти напряму. Файл `tailwind.config.js` із
`content: [...]` — залишок від v3, який v4 не читає; `autoprefixer` у devDependencies теж уже не
потрібен (Vite/esbuild додає префікси сам). Обидва — кандидат на видалення при реальному старті проєкту.

---

## Знайдена вада бойлерплейту (і чому консоль не була чистою)

Симптом одразу після клонування — помилки Vite з HTTP 500:

```
11:46:56 [vite] (client) Pre-transform error: Failed to resolve import "./utils" from "src/common/i18n.ts". Does the file exist?
```

Причина — вада самого upstream, а не середовища розробки. Коміт `625c718 fix: satisfy lint errors - more
descriptive file name required` перейменував `src/common/utils.ts` → `src/common/utilities.ts`
(0 вставлень / 0 видалень, чисте перейменування), але не оновив чотири імпорти, які вказували на стару
назву:

| Файл | Було | Стало |
| --- | --- | --- |
| `src/common/i18n.ts` | `from "./utils"` | `from "./utilities"` |
| `src/components/utils/development-tools/TanStackRouterDevelopmentTools.tsx` | `from "../../../common/utils"` | `from "../../../common/utilities"` |
| `src/components/utils/development-tools/TanStackTableDevelopmentTools.tsx` | `from "../../../common/utils"` | `from "../../../common/utilities"` |
| `src/components/utils/development-tools/ReactHookFormDevelopmentTools.tsx` | `from "../../../common/utils"` | `from "../../../common/utilities"` |

Чому це «не помітно» у автора: помилку видно лише на тих модулях, які браузер реально запитує через
dev-сервер; окрім того, у шаблоні перевірка типів «захована» в `build` (`tsc && vite build`), а не виноситься
в окрему команду після клонування. У нашому випадку `npx tsc --noEmit` теж показував ці чотири помилки,
тому виправлення підтверджено трьома незалежними перевірками: `tsc` (вихід 0), `pnpm lint` (вихід 0) і
консоль браузера (без помилок).

**Висновок для подальшої роботи:** жоден template не варта «він же клонується» — після клонування
обов'язковий прогін `tsc --noEmit` → `lint` → `dev` → консоль браузера, перш ніж робити висновок про стан
проєкту.

---

## Етап 3. Практична модифікація та доказ роботи HMR

Зміна в `src/pages/Home.tsx` — під заголовком додано рядок:

```tsx
<p className="text-white text-2xl mt-4">
  Лабораторна робота №7 — Vite + React + TypeScript
</p>
```

Збереження файлу → текст з'явився на сторінці **миттєво, без перезавантаження**. Скріншот:
`docs/screenshots/7-02-hmr-home-updated.png`.

Доказ, що відпрацював саме HMR, а не повне перезавантаження сторінки (перевірено скриптом у консолі
браузера):

1. До редагування встановлено `window.__hmrMarker = "marker-…"`; після редагування мікер
   **зберігся** — повний reload обнулив би `window`.
2. `performance.now()` до зміни — 76 858 мс, після — 108 276 мс: безперервний аптайм тієї самої
   сторінки.
3. У консолі: `[vite] hot updated: /src/pages/Home.tsx` — Vite надіслав patch через WebSocket
   (`/@vite/hmr`), і React Fast Refresh замінив лише компонент `Home`.
4. `document.querySelectorAll("p")` після оновлення повертає
   `["Hello, world!", "Лабораторна робота №7 — Vite + React + TypeScript"]`.

Механізм: `@vitejs/plugin-react-swc` вставляє в модулі реєстрацію `import.meta.hot` і обгортку
Fast Refresh; dev-сервер стежить за файлами, і на зміну публікує в веб-сокет `update`-сповіщення, а
браузер підмінює модуль у графі ES-модулів без втрати стану React.

---

## Спостереження консолі та результати перевірок

Попередження (не помилки), які залишились після виправлення імпортів:

1. `i18next` через `LanguageDetector` визначає мову браузера (`ru`) і шукає
   `src/assets/locales/ru/translations.json` → 404, далі спрацьовує `fallbackLng: "en"`. Локалі в
   шаблоні є лише для `en` і `es` — поведінка очікувана, але показова: комбінація `LanguageDetector` +
   `i18next-http-backend` дає мережевий 404 на кожен відкритий проєкт, якщо локаль користувача не підтримується.
2. `[@tanstack/router-devtools] This package has moved to @tanstack/react-router-devtools` — шаблон
   використовує застарілу назву пакета з devDependencies.
3. `[vite:react-swc] We recommend switching to @vitejs/plugin-react for improved performance as no swc
   plugins are used` — Vite 8 збіркається на rolldown, тому SWC-плагін тут додаткова, а не потрібна
   ланка; це рекомендація, не помилка.

Результати команд перевірки:

| Команда | Вихід | Коментар |
| --- | --- | --- |
| `npx tsc --noEmit` | 0 | після виправлення чотирьох імпортів |
| `pnpm lint` | 0 | `--max-warnings 0`, без попереджень |
| `pnpm build` | 0 | 200 модулів, `dist/` за 1.25 s, головний чанк 360.20 kB (113.71 kB gzip) |
| `pnpm test:unit` | 1 | «No test files found» — у шаблоні **немає** юніт-тестів у `src/`, є лише `e2e/example.spec.ts` |
| `pnpm format` | 0 | нормалізував `routeTree.gen.ts` після генерації |

Організаційна зміна: у `.gitignore` додано `/public/locales/`, бо цей каталог — артефакт плаґіна
`rollup-plugin-copy`, який створює dev-сервер і збірка, а не вихідний код.

---

## Висновки

Досліджено бойлерплейт Vite + React + TypeScript: розібрано `package.json` (19 dependencies і
45 devDependencies, 17 скриптів), `vite.config.ts` із чотирма плаґінами без жодного аліасу, точку входу
`src/main.tsx` і файлоорієнтовану маршрутизацію, де зв'язок `/ → Home` оголошений у `src/routes/index.ts`,
а `src/routeTree.gen.ts` є згенерованим кодом. Окрім очікуваного, клонування й `pnpm install` не дали
робочого проєкту: актуальний `main` upstream містив зламаний імпорт (`utils.ts` → `utilities.ts` у коміті
`625c718`), який ламав dev-сервер із HTTP 500 — усунено, перевірено `tsc`, `eslint` і консоллю браузера.
Практичну частину викладено в HMR-модифікації `src/pages/Home.tsx`: зміну відображено миттєво, а
збереження мікера в `window` і безперервний аптайм `performance.now()` доводять підміну лише компонента
`Home` без перезавантаження сторінки та без втрати стану React.
