# Technical Details

[![Ramayan CI](https://github.com/shubhattin/valmiki_ramayanam/actions/workflows/ramayan_ci.yml/badge.svg)](https://github.com/shubhattin/valmiki_ramayanam/actions/workflows/ramayan_ci.yml)
[![App Checks](https://github.com/shubhattin/valmiki_ramayanam/actions/workflows/app_checks.yml/badge.svg)](https://github.com/shubhattin/valmiki_ramayanam/actions/workflows/app_checks.yml)

## Tech Stack

### **Frontend**

- **JS Framework**: [SvelteKit](https://kit.svelte.dev/) meta framework for [Svelte](https://svelte.dev/), also using [TypeScript](https://www.typescriptlang.org/)
- **Design and Components**: [TailwindCSS](https://tailwindcss.com/) along with [Skeleton UI](https://www.skeleton.dev/)
- **Query Helper** : [Tanstack Query](https://tanstack.com/query/latest) for fetching and managing asynchronous data.

### **Backend**

- **API**: [trpc](https://trpc.io/) for API
- **Database** : [PostgreSQL](https://www.postgresql.org/) hosted on [NeonDB](https://neon.tech/) and with [Drizzle](https://orm.drizzle.team/) for ORM.
- **Authentication** : Using custom auth with JWT using [jose](https://github.com/panva/jose)
- **Hosting Provider** : [Vercel](https://vercel.com/) for hosting our website and API. As currently our backend is Edge Compatible so we are using Vercel Edge Functions for API.

## Data Processing

- _Transliteration_: [Lipi Lekhika](https://app-lipilekhika.pages.dev/)
- _Data Source_: [Valmiki Ramayanam - Wikisource](https://sa.wikisource.org/wiki/रामायणम्)
- Scripts Associated the tasks in `data/ramaayana/`:
  - `get_raw_data.py`: Fetches the data from the Wikisource and stores it in `data/ramaayana/raw_data/`. It prefers to fetch the data from the [cached zip](https://github.com/shubhattin/valmiki_ramayanam/releases/download/raw_data/raw_data.7z) instead also of directly fetching from the Wikisource(as the source might be edited which would cause inconsitent results).
  - `get_text.py`: Processes the raw data and stores the text in `data/ramaayana/text_data/`.
  - `get_json.py`: Processes the text data and stores the JSON in `data/ramaayana/data/`.
  - `make_excel_files.ts`: Processes the JSON data and stores the Excel files in `data/ramaayana/out/`.
  - `run_tests.py`: Runs the tests on the JSON data, and saves the generated test result in `data/ramayan/test_out.md`.
- [Raw Data Cached Zip of Extarcted HTML](https://github.com/shubhattin/valmiki_ramayanam/releases/download/raw_data/raw_data.7z) on [raw data release](https://github.com/shubhattin/valmiki_ramayanam/releases/tag/raw_data)
