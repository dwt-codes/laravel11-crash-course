# Laravel 11 Crash Course — App Bring-Up Procedure

This document describes the steps needed to bring the Laravel 11 application up locally.

## 1. Prepare the environment

From the project root:

```bash
cp .env.example .env
```

This creates the local environment configuration file required by Laravel.

## 2. Install PHP dependencies

```bash
composer install
```

If Composer reports incompatible packages due to the PHP version, run:

```bash
composer update
```

## 3. Generate the application key

```bash
php artisan key:generate
```

This sets `APP_KEY` in the `.env` file.

## 4. Create the SQLite database file

```bash
touch database/database.sqlite
```

If you are using a different database driver, update the `.env` values accordingly.

## 5. Run database migrations

```bash
php artisan migrate
```

This creates the required tables for users, sessions, jobs, notes, and cache.

## 6. Install JavaScript dependencies

```bash
npm install
```

If you encounter a Rollup/npm optional dependency error on ARM or other systems, remove the existing frontend installation and reinstall:

```bash
rm -rf node_modules package-lock.json
npm install
```

## 7. Start the development servers

Open two terminals.

Terminal 1:

```bash
php artisan serve
```

Terminal 2:

```bash
npm run dev
```

## 8. Access the application

Open the browser at:

- Backend: `http://127.0.0.1:8000`
- Vite assets: `http://localhost:5174`

## Notes

- The `.env` file should not be committed to version control.
- If you are using a non-SQLite database, update `DB_CONNECTION`, `DB_HOST`, `DB_DATABASE`, `DB_USERNAME`, and `DB_PASSWORD` in `.env` before running migrations.
- If Laravel cannot start because `vendor/autoload.php` is missing, install Composer dependencies first.
