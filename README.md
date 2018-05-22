# Sekolah

[![Join the chat at https://gitter.im/sekolah/Lobby](https://badges.gitter.im/sekolah/Lobby.svg)](https://gitter.im/sekolah/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/bantenprov/sekolah/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/sekolah/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/bantenprov/sekolah/badges/build.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/sekolah/build-status/master)
[![Latest Stable Version](https://poser.pugx.org/bantenprov/sekolah/v/stable)](https://packagist.org/packages/bantenprov/sekolah)
[![Total Downloads](https://poser.pugx.org/bantenprov/sekolah/downloads)](https://packagist.org/packages/bantenprov/sekolah)
[![Latest Unstable Version](https://poser.pugx.org/bantenprov/sekolah/v/unstable)](https://packagist.org/packages/bantenprov/sekolah)
[![License](https://poser.pugx.org/bantenprov/sekolah/license)](https://packagist.org/packages/bantenprov/sekolah)
[![Monthly Downloads](https://poser.pugx.org/bantenprov/sekolah/d/monthly)](https://packagist.org/packages/bantenprov/sekolah)
[![Daily Downloads](https://poser.pugx.org/bantenprov/sekolah/d/daily)](https://packagist.org/packages/bantenprov/sekolah)

Sekolah

### Install via composer

- Development snapshot

```bash
composer require bantenprov/sekolah:dev-master
```

- Latest release:

```bash
composer require bantenprov/sekolah
```

### Download via github

```bash
git clone https://github.com/bantenprov/sekolah.git
```

#### Edit `config/app.php` :

```php
'providers' => [
    /*
    * Laravel Framework Service Providers...
    */
    Illuminate\Auth\AuthServiceProvider::class,
    Illuminate\Broadcasting\BroadcastServiceProvider::class,
    Illuminate\Bus\BusServiceProvider::class,
    Illuminate\Cache\CacheServiceProvider::class,
    Illuminate\Foundation\Providers\ConsoleSupportServiceProvider::class,
    Illuminate\Cookie\CookieServiceProvider::class,
    //...
    Bantenprov\Sekolah\SekolahServiceProvider::class,
    //...
],
```

#### Edit `app/Http/Kernel.php`

```php
protected $routeMiddleware = [
    'auth' => \Illuminate\Auth\Middleware\Authenticate::class,
    'auth.basic' => \Illuminate\Auth\Middleware\AuthenticateWithBasicAuth::class,
    'bindings' => \Illuminate\Routing\Middleware\SubstituteBindings::class,
    'can' => \Illuminate\Auth\Middleware\Authorize::class,
    'guest' => \App\Http\Middleware\RedirectIfAuthenticated::class,
    'throttle' => \Illuminate\Routing\Middleware\ThrottleRequests::class,
    //...
    'role' => \Laratrust\Middleware\LaratrustRole::class,
    'permission' => \Laratrust\Middleware\LaratrustPermission::class,
    'ability' => \Laratrust\Middleware\LaratrustAbility::class,
    //...
];
```

#### Lakukan migrate :

```bash
php artisan migrate
```

#### Lakukan publish semua komponen :

```bash
php artisan vendor:publish --tag=sekolah-publish
```

#### Lakukan auto dump :

```bash
composer dump-autoload
```

#### Lakukan seeding :

- Seeding semua seeder

```bash
php artisan db:seed --class=BantenprovSekolahSeeder
```

- Seeding secara individual

```bash
php artisan db:seed --class=BantenprovSekolahSeederJenisSekolah
php artisan db:seed --class=BantenprovSekolahSeederSekolah
php artisan db:seed --class=BantenprovSekolahSeederProdiSekolah
```

#### Edit menu `resources/assets/js/menu.js`

```javascript
{
    name: 'Dashboard',
    icon: 'fa fa-dashboard',
    childType: 'collapse',
    childItem: [
        //...
        // Sekolah
        {
            name: 'Sekolah',
            link: '/dashboard/sekolah',
            icon: 'fa fa-angle-double-right',
        },
        // Prodi Sekolah
        {
            name: 'Prodi Sekolah',
            link: '/dashboard/prodi-sekolah',
            icon: 'fa fa-angle-double-right',
        },
        //...
        // Admin Sekolah
        {
            name: 'Admin Sekolah',
            link: '/dashboard/admin-sekolah',
            icon: 'fa fa-angle-double-right',
        },
        //...
    ]
},
```

```javascript
{
    name: 'Admin',
    icon: 'fa fa-lock',
    childType: 'collapse',
    childItem: [
        //...
        // Sekolah
        {
            name: 'Sekolah',
            link: '/admin/sekolah',
            icon: 'fa fa-angle-double-right',
        },
        // Prodi Sekolah
        {
            name: 'Prodi Sekolah',
            link: '/admin/prodi-sekolah',
            icon: 'fa fa-angle-double-right',
        },
        // Admin Sekolah
        {
          name: 'Admin Sekolah',
          link: '/admin/admin-sekolah',
          icon: 'fa fa-angle-double-right',
        },
        //...
    ]
},
```

#### Tambahkan components `resources/assets/js/components.js` :

```javascript
//... Jenis Sekolah ...//

import JenisSekolahAdminShow from '~/components/bantenprov/sekolah/jenis-sekolah/JenisSekolahAdmin.show.vue';
Vue.component('jenis-sekolah-admin', JenisSekolahAdminShow);

//... Echarts Jenis Sekolah ...//

import JenisSekolah from '~/components/bantenprov/sekolah/jenis-sekolah/JenisSekolah.chart.vue';
Vue.component('jenis-sekolah-echarts', JenisSekolah);

import JenisSekolahKota from '~/components/bantenprov/sekolah/jenis-sekolah/JenisSekolahKota.chart.vue';
Vue.component('jenis-sekolah-echarts-kota', JenisSekolahKota);

import JenisSekolahTahun from '~/components/bantenprov/sekolah/jenis-sekolah/JenisSekolahTahun.chart.vue';
Vue.component('jenis-sekolah-echarts-tahun', JenisSekolahTahun);

//... Mini Bar Charts Jenis Sekolah ...//

import JenisSekolahBar01 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahBar01.vue';
Vue.component('jenis-sekolah-bar-01', JenisSekolahBar01);

import JenisSekolahBar02 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahBar02.vue';
Vue.component('jenis-sekolah-bar-02', JenisSekolahBar02);

import JenisSekolahBar03 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahBar03.vue';
Vue.component('jenis-sekolah-bar-03', JenisSekolahBar03);

//... Mini Pie Charts Jenis Sekolah ...//

import JenisSekolahPie01 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahPie01.vue';
Vue.component('jenis-sekolah-pie-01', JenisSekolahPie01);

import JenisSekolahPie02 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahPie02.vue';
Vue.component('jenis-sekolah-pie-02', JenisSekolahPie02);

import JenisSekolahPie03 from '~/components/views/bantenprov/sekolah/jenis-sekolah/JenisSekolahPie03.vue';
Vue.component('jenis-sekolah-pie-03', JenisSekolahPie03);

//... Sekolah ...//

import SekolahAdminShow from '~/components/bantenprov/sekolah/sekolah/SekolahAdmin.show.vue';
Vue.component('sekolah-admin', SekolahAdminShow);

//... Echarts Sekolah ...//

import Sekolah from '~/components/bantenprov/sekolah/sekolah/Sekolah.chart.vue';
Vue.component('sekolah-echarts', Sekolah);

import SekolahKota from '~/components/bantenprov/sekolah/sekolah/SekolahKota.chart.vue';
Vue.component('sekolah-echarts-kota', SekolahKota);

import SekolahTahun from '~/components/bantenprov/sekolah/sekolah/SekolahTahun.chart.vue';
Vue.component('sekolah-echarts-tahun', SekolahTahun);

//... Mini Bar Charts Sekolah ...//

import SekolahBar01 from '~/components/views/bantenprov/sekolah/sekolah/SekolahBar01.vue';
Vue.component('sekolah-bar-01', SekolahBar01);

import SekolahBar02 from '~/components/views/bantenprov/sekolah/sekolah/SekolahBar02.vue';
Vue.component('sekolah-bar-02', SekolahBar02);

import SekolahBar03 from '~/components/views/bantenprov/sekolah/sekolah/SekolahBar03.vue';
Vue.component('sekolah-bar-03', SekolahBar03);

//... Mini Pie Charts Sekolah ...//

import SekolahPie01 from '~/components/views/bantenprov/sekolah/sekolah/SekolahPie01.vue';
Vue.component('sekolah-pie-01', SekolahPie01);

import SekolahPie02 from '~/components/views/bantenprov/sekolah/sekolah/SekolahPie02.vue';
Vue.component('sekolah-pie-02', SekolahPie02);

import SekolahPie03 from '~/components/views/bantenprov/sekolah/sekolah/SekolahPie03.vue';
Vue.component('sekolah-pie-03', SekolahPie03);

//... Prodi Sekolah ...//

import ProdiSekolahAdminShow from '~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolahAdmin.show.vue';
Vue.component('prodi-sekolah-admin', ProdiSekolahAdminShow);

//... Echarts Prodi Sekolah ...//

import ProdiSekolah from '~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolah.chart.vue';
Vue.component('prodi-sekolah-echarts', ProdiSekolah);

import ProdiSekolahKota from '~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolahKota.chart.vue';
Vue.component('prodi-sekolah-echarts-kota', ProdiSekolahKota);

import ProdiSekolahTahun from '~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolahTahun.chart.vue';
Vue.component('prodi-sekolah-echarts-tahun', ProdiSekolahTahun);

//... Mini Bar Charts Prodi Sekolah ...//

import ProdiSekolahBar01 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahBar01.vue';
Vue.component('prodi-sekolah-bar-01', ProdiSekolahBar01);

import ProdiSekolahBar02 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahBar02.vue';
Vue.component('prodi-sekolah-bar-02', ProdiSekolahBar02);

import ProdiSekolahBar03 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahBar03.vue';
Vue.component('prodi-sekolah-bar-03', ProdiSekolahBar03);

//... Mini Pie Charts Prodi Sekolah ...//

import ProdiSekolahPie01 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahPie01.vue';
Vue.component('prodi-sekolah-pie-01', ProdiSekolahPie01);

import ProdiSekolahPie02 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahPie02.vue';
Vue.component('prodi-sekolah-pie-02', ProdiSekolahPie02);

import ProdiSekolahPie03 from '~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahPie03.vue';
Vue.component('prodi-sekolah-pie-03', ProdiSekolahPie03);

//... Admin Sekolah ...//

import AdminSekolahAdminShow from '~/components/bantenprov/sekolah/admin-sekolah/AdminSekolahAdmin.show.vue';
Vue.component('admin-sekolah-admin', AdminSekolahAdminShow);

//... Echarts Admin Sekolah ...//

import AdminSekolah from '~/components/bantenprov/sekolah/admin-sekolah/AdminSekolah.chart.vue';
Vue.component('admin-sekolah-echarts', AdminSekolah);

import AdminSekolahKota from '~/components/bantenprov/sekolah/admin-sekolah/AdminSekolahKota.chart.vue';
Vue.component('admin-sekolah-echarts-kota', AdminSekolahKota);

import AdminSekolahTahun from '~/components/bantenprov/sekolah/admin-sekolah/AdminSekolahTahun.chart.vue';
Vue.component('admin-sekolah-echarts-tahun', AdminSekolahTahun);

//... Mini Bar Charts Admin Sekolah ...//

import AdminSekolahBar01 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahBar01.vue';
Vue.component('admin-sekolah-bar-01', AdminSekolahBar01);

import AdminSekolahBar02 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahBar02.vue';
Vue.component('admin-sekolah-bar-02', AdminSekolahBar02);

import AdminSekolahBar03 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahBar03.vue';
Vue.component('admin-sekolah-bar-03', AdminSekolahBar03);

//... Mini Pie Charts Admin Sekolah ...//

import AdminSekolahPie01 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahPie01.vue';
Vue.component('admin-sekolah-pie-01', AdminSekolahPie01);

import AdminSekolahPie02 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahPie02.vue';
Vue.component('admin-sekolah-pie-02', AdminSekolahPie02);

import AdminSekolahPie03 from '~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahPie03.vue';
Vue.component('admin-sekolah-pie-03', AdminSekolahPie03);
```

#### Tambahkan route di dalam file : `resources/assets/js/routes.js` :

```javascript
{
    path: '/dashboard',
    redirect: '/dashboard/home',
    component: layout('Default'),
    children: [
        //...
        // Sekolah
        {
            path: '/dashboard/sekolah',
            components: {
                main: resolve => require(['~/components/views/bantenprov/sekolah/sekolah/SekolahDashboard.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Sekolah",
            },
        },
        // Prodi Sekolah
        {
            path: '/dashboard/prodi-sekolah',
            components: {
                main: resolve => require(['~/components/views/bantenprov/sekolah/prodi-sekolah/ProdiSekolahDashboard.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Prodi Sekolah",
            },
        },
        // Admin Sekolah
        {
            path: '/dashboard/admin-sekolah',
            components: {
                main: resolve => require(['~/components/views/bantenprov/sekolah/admin-sekolah/AdminSekolahDashboard.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Admin Sekolah",
            },
        },
        //...
    ]
},
```

```javascript
{
    path: '/admin',
    redirect: '/admin/dashboard/home',
    component: layout('Default'),
    children: [
        //...
        // Sekolah
        {
            path: '/admin/sekolah',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/sekolah/Sekolah.index.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Sekolah",
            },
        },
        {
            path: '/admin/sekolah/create',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/sekolah/Sekolah.add.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Add Sekolah",
            },
        },
        {
            path: '/admin/sekolah/:id',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/sekolah/Sekolah.show.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "View Sekolah",
            },
        },
        {
            path: '/admin/sekolah/:id/edit',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/sekolah/Sekolah.edit.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Edit Sekolah",
            },
        },
        // Prodi Sekolah
        {
            path: '/admin/prodi-sekolah',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolah.index.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Prodi Sekolah",
            },
        },
        {
            path: '/admin/prodi-sekolah/create',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolah.add.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Add Prodi Sekolah",
            },
        },
        {
            path: '/admin/prodi-sekolah/:id',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolah.show.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "View Prodi Sekolah",
            },
        },
        {
            path: '/admin/prodi-sekolah/:id/edit',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/prodi-sekolah/ProdiSekolah.edit.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Edit Prodi Sekolah",
            },
        },
        // Admin Sekolah
        {
            path: '/admin/admin-sekolah',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/admin-sekolah/AdminSekolah.index.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Admin Sekolah",
            },
        },
        {
            path: '/admin/admin-sekolah/create',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/admin-sekolah/AdminSekolah.add.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Add Admin Sekolah",
            },
        },
        {
            path: '/admin/admin-sekolah/:id',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/admin-sekolah/AdminSekolah.show.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "View Admin Sekolah",
            },
        },
        {
            path: '/admin/admin-sekolah/:id/edit',
            components: {
                main: resolve => require(['~/components/bantenprov/sekolah/admin-sekolah/AdminSekolah.edit.vue'], resolve),
                navbar: resolve => require(['~/components/Navbar.vue'], resolve),
                sidebar: resolve => require(['~/components/Sidebar.vue'], resolve),
            },
            meta: {
                title: "Edit Admin Sekolah",
            },
        },
        //...
    ]
},
```
