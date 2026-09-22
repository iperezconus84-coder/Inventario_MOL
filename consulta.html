const CACHE_NAME = 'imol-terreno-v2';

// Archivos locales y CDNs externos que necesitamos guardar en la memoria caché del teléfono
const urlsToCache = [
    './',
    './consulta.html',
    './manifest.json',
    './icon-192x192.png',
    './icon-512x512.png',
    // Librerías externas (esencial para que funcione offline completo)
    'https://cdn.tailwindcss.com',
    'https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js',
    'https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js',
    'https://unpkg.com/@zxing/library@latest'
];

// 1. INSTALACIÓN: Descarga y guarda todos los archivos necesarios
self.addEventListener('install', event => {
    event.waitUntil(
        caches.open(CACHE_NAME)
            .then(cache => {
                console.log('Cache abierta');
                // Usamos catch para que si un ícono o archivo falla, no detenga toda la instalación
                return Promise.allSettled(
                    urlsToCache.map(url => cache.add(url).catch(err => console.warn('No se pudo cachear:', url, err)))
                );
            })
    );
});

// 2. ACTIVACIÓN: Limpia cachés antiguas si cambias la versión de la app
self.addEventListener('activate', event => {
    const cacheWhitelist = [CACHE_NAME];
    event.waitUntil(
        caches.keys().then(cacheNames => {
            return Promise.all(
                cacheNames.map(cacheName => {
                    if (cacheWhitelist.indexOf(cacheName) === -1) {
                        return caches.delete(cacheName);
                    }
                })
            );
        })
    );
});

// 3. INTERCEPCIÓN (El Modo Offline): Busca primero en caché, si no está, va a internet
self.addEventListener('fetch', event => {
    event.respondWith(
        caches.match(event.request)
            .then(response => {
                // Si el archivo está en la caché, lo devuelve (Offline)
                if (response) {
                    return response;
                }
                // Si no está, lo busca en internet
                return fetch(event.request).then(
                    function(networkResponse) {
                        // Verifica si es una respuesta válida antes de cachearla al vuelo
                        if(!networkResponse || networkResponse.status !== 200 || networkResponse.type !== 'basic') {
                            return networkResponse;
                        }
                        
                        // Opcional: Clonar y cachear archivos nuevos que se vayan encontrando
                        var responseToCache = networkResponse.clone();
                        caches.open(CACHE_NAME)
                            .then(function(cache) {
                                cache.put(event.request, responseToCache);
                            });

                        return networkResponse;
                    }
                );
            })
    );
});
