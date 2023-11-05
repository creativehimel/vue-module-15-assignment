## Integration with Laravel:

---

Creating a basic project using Laravel and Inertia.js is a straightforward process. I'll guide you through the steps to set up a simple web application that includes at least one page managed by Inertia.js. In this example, we'll create a basic task management application.

### Step 1: Set up Laravel Project

---

- Create a new Laravel Project:

```
composer create-project laravel/laravel example-app
```

### Step 2: Set up Inertia.js and Vue.js

---

```
composer require inertiajs/inertia-laravel
```

### Step 3: Setup Laravel for vue.js

---

- update middleware

```
php artisan inertia:middleware
```

- modify `/app/http/kernel.php`

```
 'web' => [
      // ...
      \App\Http\Middleware\HandleInertiaRequests::class,
   ],
```

### Step 4: Root template

---

- update `/resources/js/app.js`

```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});
```

### Step 5: Setup vue with vite

---

```
   npm install @inertiajs/vue3
   npm i @vitejs/plugin-vue
```

- update `/resources/js/app.js`

```
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';

export default defineConfig({
    plugins: [
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
});
```

- update `/vite.config.js`

```
import vue from '@vitejs/plugin-vue'

export default {
    plugins: [
        vue(),
        laravel({
            input: ['resources/css/app.css', 'resources/js/app.js'],
            refresh: true,
        }),
    ],
}
```

### Step 6: Create Vue Application

---

- create a Directory `resources/js/Pages/`
- create test component `resources/js/Pages/Welcome.vue`

```
<script setup>
import {ref, reactive} from 'vue'

</script>


<template>

<div>Welcome</div>

</template>

<style scoped>

</style>
```

### Step 7: Update Home route with new sample vue component

---

- update `routes/web.php`:

```

use Inertia\Inertia;

Route::get('/', function(){
    return Inertia::render(component:'Welcome');
});

```

### Step 8: Run the Application

---

- Compile the assets:

```
npm run dev
```

- Start the development server:

```
php artisan serve
```

- Visit [http://localhost:8000](http://localhost:8000) inyour browser to see the blog posts.

You've now set up a basic Laravel project with Inertia.js and created a simple web application with at least one page managed by Inertia.js. This example illustrates how Inertia.js seamlessly integrates with Laravel, allowing you to build dynamic, client-side interactive web applications while utilizing the power of Laravel on the backend.
