# parcial
# 🌱 Tend Agro - Plataforma de Monitoreo Urbano (DDD Architecture)

Este proyecto es una aplicación web frontend interactiva construida con **Vue 3 (Composition API)** y **Vite**, diseñada bajo los lineamientos de **Domain-Driven Design (DDD)**. La plataforma está adaptada específicamente para el **Caso Tend**, permitiendo la gestión, visualización y edición en memoria de parcelas urbanas, así como el registro técnico de inspecciones manuales agrícolas con soporte internacional multi-idioma.

---

## 🚀 Tecnologías y Librerías Utilizadas

* **Vue 3 & Vite:** Entorno de desarrollo ultrarrápido y framework progresivo utilizando `<script setup>`.
* **Vue-i18n (v9):** Librería oficial del ecosistema de Vue para la internacionalización y traducción reactiva en tiempo real (ES / EN).
* **JavaScript Moderno (ES6+):** Programación orientada a objetos para el desacoplamiento de capas del dominio.
* **Flexbox & CSS Grid:** Maquetación responsiva premium con variables dinámicas inspiradas en Tailwind.

---

## 📂 Estructura del Proyecto e Inyección de Capas

El proyecto sigue una división estricta de responsabilidades para asegurar que el núcleo de negocio sea agnóstico a la tecnología de persistencia:

```text
untitled2/ (Raíz del Proyecto)
├── server/
│   └── db.json               # Base de datos simulada (Estructura inicial del Caso)
├── index.html                # Punto de entrada al DOM del navegador
├── package.json              # Gestión de dependencias y scripts de arranque
└── src/
    ├── main.js               # Inicializador global del framework e inyección de plugins (i18n)
    ├── App.vue               # Componente Raíz (Layout, Navbar Reactivo y Footer Corporativo)
    └── product/
        ├── domain/           # 🏢 CAPA DE DOMINIO (Reglas de negocio puras, sin frameworks)
        │   ├── models/
        │   │   └── Product.js       # Entidad del Dominio (Mapeo, getters y validaciones estrictas)
        │   └── repository/
        │       └── ProductRepository.js # Contrato/Interfaz que define las operaciones permitidas
        ├── infrastructure/   # 🔌 CAPA DE INFRAESTRUCTURA (Conexión externa y persistencia)
        │   └── data-sources/
        │       └── FakeProductApi.js # Implementación local en memoria del Repositorio (Mapea db.json)
        └── presentation/     # 🎨 CAPA DE PRESENTACIÓN (Interfaz de usuario y reactividad de Vue)
            ├── components/
            │   └── ProductCard.vue   # Tarjeta visual para el renderizado de parcelas
            ├── store/
            │   └── locale.js         # Diccionario centralizado y configuración de idiomas de i18n
            └── views/
                ├── HomeView.vue      # Tablero/Grid de parcelas con Modales de Edición y Detalles Técnicos
                └── FormView.vue      # Formulario de captura para Inspecciones Manuales Agrícolas

## 🚨 Mapeo de Emergencia para el Examen (Ruta de Archivos Exacta)

Si necesitas reconfigurar el proyecto rápidamente durante la evaluación, los cambios se encuentran en las siguientes ubicaciones:

### 1. Cambiar el Nombre del Proyecto
* **Nombre Técnico (npm):** 📂 Ubicación: Raíz del proyecto -> 📄 Archivo: `package.json`
  *Acción:* Cambia el valor de la propiedad `"name"` en la línea 2.
* **Nombre Comercial en la Barra de Navegación (UI):** 📂 Ubicación: `src/` -> 📄 Archivo: `App.vue`
  *Acción:* Busca la etiqueta `<div class="nav-brand">` en la línea 20 aprox. y edita el texto Tend Agro.

### 2. Cambiar la URL si te dan una Fake API Externa
* **Configuración de Endpoints:** 📂 Ubicación: `src/product/infrastructure/data-sources/` -> 📄 Archivo: `FakeProductApi.js`
  *Acción:* Ve al `constructor()` y reemplaza las direcciones HTTP por las URLs externas que te dicte el profesor:
  ```javascript
  this.plotsUrl = '[https://api-externa.com/nuevos-datos](https://api-externa.com/nuevos-datos)';
  this.inspectionsUrl = '[https://api-externa.com/guardar](https://api-externa.com/guardar)';
