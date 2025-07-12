# Tasks App - My First Vue.js Project

A simple and clean task management application built with Vue 3, TypeScript, and Vite. This is my first Vue.js application, showcasing fundamental Vue concepts and modern development practices.

## 🚀 Features

- ✅ **Add Tasks**: Create new tasks with a simple form
- ✅ **Toggle Completion**: Mark tasks as completed or incomplete
- ✅ **Delete Tasks**: Remove tasks you no longer need
- ✅ **Filter Tasks**: View all tasks, only incomplete tasks, or only completed tasks
- ✅ **Progress Tracking**: See completion progress with a counter
- ✅ **Responsive Design**: Works on desktop and mobile devices

## 🛠️ Tech Stack

- **Vue 3** - Progressive JavaScript framework
- **TypeScript** - Type-safe JavaScript
- **Vite** - Fast build tool and development server
- **Composition API** - Modern Vue 3 approach for component logic
- **CSS3** - Custom styling without external frameworks

## 📁 Project Structure

```
src/
├── App.vue              # Main application component
├── components/
│   ├── TaskForm.vue     # Form for adding new tasks
│   ├── TasksList.vue    # List of tasks with actions
│   └── FilterButton.vue # Filter buttons for task views
├── types.ts             # TypeScript type definitions
├── main.ts              # Application entry point
└── style.css            # Global styles
```

## 🏃‍♂️ Getting Started

### Prerequisites

- Node.js (v18 or higher)
- pnpm (recommended) or npm

### Installation

1. Clone the repository:
```bash
git clone git@github.com:Amar2Kk/tasks-app.git
cd tasks-app
```

2. Install dependencies:
```bash
pnpm install
# or
npm install
```

3. Start the development server:
```bash
pnpm dev
# or
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

### Build for Production

```bash
pnpm build
# or
npm run build
```

### Preview Production Build

```bash
pnpm preview
# or
npm run preview
```

## 🎯 Key Vue.js Concepts Learned

This project demonstrates several important Vue 3 concepts:

### Composition API
- Using `ref()` for reactive state management
- Using `computed()` for derived state
- Using `<script setup>` syntax for cleaner component code

### Component Communication
- **Props**: Passing data from parent to child components
- **Events**: Child components emitting events to parent (`@addTask`, `@toggleComplete`, `@deleteTask`)
- **Custom Events**: Creating and handling custom component events

### Reactive State Management
- Managing task list state with `ref()`
- Computing filtered tasks and completion statistics
- Updating UI automatically when state changes

### TypeScript Integration
- Defining interfaces for data structures (`Task`, `TaskFilter`)
- Type-safe component props and events
- Better development experience with IntelliSense

## 📝 Component Breakdown

### App.vue
The main component that:
- Manages the global state (tasks array, current filter)
- Handles all task operations (add, toggle, delete)
- Renders child components and passes data/handlers

### TaskForm.vue
A form component that:
- Handles new task input
- Emits `addTask` event to parent
- Validates input before submission

### TasksList.vue
Displays the list of tasks and:
- Renders each task with completion status
- Provides toggle and delete actions
- Handles empty state

### FilterButton.vue
A reusable button component that:
- Shows different filter options
- Highlights the currently active filter
- Emits filter change events

## 🚧 Future Enhancements

Potential features to add as I continue learning Vue.js:

- [ ] **Persistence**: Save tasks to localStorage
- [ ] **Task Editing**: Edit existing task titles
- [ ] **Due Dates**: Add and display task deadlines
- [ ] **Drag & Drop**: Reorder tasks

## 📚 Learning Resources

Resources that helped me build this app:

- [Synatx : Modern Vue.js Crash Course 2025](https://youtu.be/5oKpoqmUj64)
---

**Note**: This is my first Vue.js application, built as a learning exercise to understand Vue 3 fundamentals, the Composition API, and modern JavaScript development practices.
