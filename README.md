# 📋 SantiagoList

> Sistema de gestión de tareas moderno y elegante con interfaz responsive y diseño glassmorphism

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwind-css&logoColor=white)

## 📖 Descripción

SantiagoList es una aplicación web SPA (Single Page Application) para la gestión inteligente de tareas. Ofrece una interfaz moderna con efectos visuales avanzados, diseño responsive y total integración con una API RESTful backend.

## ✨ Características Principales

### 🎨 Interfaz de Usuario
- **Diseño Glassmorphism**: Efectos de vidrio esmerilado con blur y transparencias
- **Gradientes Animados**: Fondo con gradiente multicolor animado
- **Animaciones Suaves**: Transiciones fluidas en todos los elementos interactivos
- **Responsive Design**: Adaptable a dispositivos móviles, tablets y escritorio
- **Tipografía Inter**: Fuente moderna y legible de Google Fonts

### 🎯 Funcionalidades

#### Gestión de Tareas
- ✅ **Crear tareas** con título, descripción, prioridad, fecha límite y etiquetas
- 🔄 **Actualizar estados**: Pendiente, En Progreso, Completada, Cancelada
- 🗑️ **Eliminar tareas** individuales o todas a la vez
- 🔍 **Búsqueda en tiempo real** con debounce de 300ms
- 🎚️ **Filtrado por estado** para organizar visualización

#### Sistema de Prioridades
- 🟢 **Baja**: Tareas sin urgencia
- 🔵 **Media**: Prioridad estándar (por defecto)
- 🟠 **Alta**: Requiere atención pronto
- 🔴 **Urgente**: Máxima prioridad

#### Dashboard de Estadísticas
- 📊 Contador de tareas totales
- ⏳ Tareas pendientes
- ▶️ Tareas en progreso
- ✅ Tareas completadas
- ❌ Tareas canceladas

### 🔌 Conectividad
- **Indicador de conexión**: Muestra estado de la API en tiempo real
- **Verificación automática**: Chequeo cada 5 segundos
- **Manejo de errores**: Notificaciones toast para feedback al usuario

## 🏗️ Arquitectura

### Estructura de Layout

```
┌─────────────────────────────────────────┐
│           Header + Connection           │
├─────────────────────────────────────────┤
│         Statistics Dashboard            │
├─────────────────────────────────────────┤
│         Task Creation Form              │
│      (Grid 3 columnas horizontal)       │
├─────────────────────────────────────────┤
│      Search & Filters Bar               │
├─────────────────────────────────────────┤
│          Task Grid (2 columns)          │
│  ┌──────────────┐  ┌──────────────┐   │
│  │   Task 1     │  │   Task 2     │   │
│  └──────────────┘  └──────────────┘   │
│  ┌──────────────┐  ┌──────────────┐   │
│  │   Task 3     │  │   Task 4     │   │
│  └──────────────┘  └──────────────┘   │
└─────────────────────────────────────────┘
```

### Tecnologías Utilizadas

| Tecnología | Propósito |
|------------|-----------|
| **HTML5** | Estructura semántica |
| **CSS3** | Estilos avanzados y animaciones |
| **JavaScript ES6+** | Lógica de aplicación |
| **Tailwind CSS** (CDN) | Framework CSS utility-first |
| **Inter Font** | Tipografía moderna |
| **Fetch API** | Comunicación con backend |

## 🚀 Instalación y Uso

### Requisitos Previos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Conexión a internet (para CDN de Tailwind y fuente Inter)
- Backend API corriendo en `https://proyecto-caso-testigo-perez-carvajal.onrender.com`

### Configuración

1. **Clonar el repositorio**
```bash
git clone <repository-url>
cd task-manager-pro
```

2. **Configurar URL del Backend**

Editar el archivo HTML y actualizar la constante `API_URL`:

```javascript
const API_URL = 'https://tu-backend-api.com';
```

3. **Abrir en el navegador**
```bash
# Opción 1: Abrir directamente el archivo
open index.html

# Opción 2: Usar servidor local
python -m http.server 8000
# Luego visitar http://localhost:8000
```

## 📡 Integración con API

### Endpoints Utilizados

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| `GET` | `/health` | Verificar estado de la API |
| `GET` | `/tasks` | Obtener todas las tareas |
| `GET` | `/tasks?status={STATUS}` | Filtrar tareas por estado |
| `GET` | `/tasks/stats` | Obtener estadísticas |
| `GET` | `/tasks/search?q={QUERY}` | Buscar tareas |
| `POST` | `/tasks` | Crear nueva tarea |
| `PATCH` | `/tasks/{id}/status?status={STATUS}` | Actualizar estado |
| `DELETE` | `/tasks/{id}` | Eliminar tarea específica |
| `DELETE` | `/tasks` | Eliminar todas las tareas |

### Estructura de Datos

**Request - Crear Tarea:**
```json
{
  "title": "Completar proyecto",
  "description": "Finalizar documentación y tests",
  "priority": 3,
  "due_date": "2025-12-31",
  "tags": ["trabajo", "urgente"]
}
```

**Response - Tarea:**
```json
{
  "id": "uuid-v4",
  "title": "Completar proyecto",
  "description": "Finalizar documentación y tests",
  "status": "PENDING",
  "priority": 3,
  "due_date": "2025-12-31",
  "tags": ["trabajo", "urgente"],
  "created_at": "2025-11-19T10:30:00Z",
  "updated_at": "2025-11-19T10:30:00Z"
}
```

**Response - Estadísticas:**
```json
{
  "total": 15,
  "pending": 5,
  "in_progress": 3,
  "completed": 6,
  "cancelled": 1
}
```

## 🎨 Personalización de Estilos

### Variables CSS Principales

```css
/* Gradiente de fondo animado */
background: linear-gradient(135deg, 
  #667eea 0%, 
  #764ba2 25%, 
  #f093fb 50%, 
  #4facfe 75%, 
  #00f2fe 100%
);

/* Colores de prioridad */
.priority-low: #10b981 (Verde)
.priority-medium: #3b82f6 (Azul)
.priority-high: #f59e0b (Naranja)
.priority-urgent: #ef4444 (Rojo)
```

### Modificar Animaciones

```css
/* Velocidad de animación de gradiente */
animation: gradientShift 15s ease infinite;

/* Duración de hover effects */
transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
```

## 🔧 Funciones JavaScript Principales

### Inicialización
```javascript
document.addEventListener('DOMContentLoaded', () => {
  checkConnection();      // Verificar conexión
  loadTasks();           // Cargar tareas
  loadStats();           // Cargar estadísticas
  setupEventListeners(); // Configurar eventos
});
```

### Gestión de Estado
```javascript
// Crear tarea
await apiCall('/tasks', { 
  method: 'POST', 
  body: JSON.stringify(taskData) 
});

// Actualizar estado
await apiCall(`/tasks/${taskId}/status?status=${newStatus}`, { 
  method: 'PATCH' 
});

// Eliminar tarea
await apiCall(`/tasks/${taskId}`, { 
  method: 'DELETE' 
});
```

### Búsqueda con Debounce
```javascript
function handleSearch(e) {
  clearTimeout(searchTimeout);
  const query = e.target.value.trim();
  
  searchTimeout = setTimeout(async () => {
    tasks = await apiCall(`/tasks/search?q=${encodeURIComponent(query)}`);
    renderTasks(tasks);
  }, 300);
}
```

## 🔒 Seguridad

- ✅ **Escape HTML**: Prevención de XSS mediante `escapeHtml()`
- ✅ **Validación Frontend**: Validación de longitud y formato
- ✅ **CORS Configurado**: Credenciales incluidas en requests
- ✅ **Confirmación de Eliminación**: Diálogos de confirmación para acciones destructivas

## 📱 Responsive Breakpoints

```css
/* Mobile First */
Default: < 768px (1 columna)

/* Tablet */
md: ≥ 768px (2 columnas en stats, 2 columnas en tareas)

/* Desktop */
lg: ≥ 1024px (3 columnas en formulario, 2 columnas en tareas)
```

## 🐛 Manejo de Errores

### Toast Notifications
```javascript
showToast('✅ Tarea creada exitosamente');
showToast('❌ Error en la petición');
```

### Logging
```javascript
console.log('Loading tasks...');
console.error('Failed to load tasks:', error);
console.warn('Validation failed: invalid title');
```

## 🎯 Próximas Mejoras

- [ ] Modo oscuro/claro
- [ ] Drag & drop para reordenar tareas
- [ ] Categorías personalizadas
- [ ] Exportar tareas a CSV/JSON
- [ ] Notificaciones push para fechas límite
- [ ] Sistema de subtareas
- [ ] Integración con calendario
- [ ] Modo offline con LocalStorage

⭐ Si este proyecto te fue útil, considera darle una estrella en GitHub

**Hecho con ❤️ y ☕**
