# React + Vite + shadcn/ui + TanStack Router

A modern React application built with Vite, featuring TanStack Router for file-based routing, shadcn/ui components, and Tailwind CSS styling.

## 🚀 Tech Stack

- **Framework**: React 19.1.1
- **Build Tool**: Vite 6.3.5 
- **Styling**: Tailwind CSS v4 with shadcn/ui components
- **Routing**: TanStack Router with file-based routing
- **Language**: TypeScript with strict configuration
- **Testing**: Vitest with jsdom environment
- **Package Manager**: pnpm

## 📦 Key Dependencies

- **UI Components**: shadcn/ui (New York style) with Radix UI primitives
- **Icons**: Lucide React
- **Styling**: Tailwind CSS v4, class-variance-authority, clsx, tailwind-merge
- **Router**: TanStack Router with devtools
- **Development**: React DevTools, TypeScript, Vitest

## 🛠️ Getting Started

### Prerequisites
- Node.js (latest LTS recommended)
- pnpm package manager

### Installation & Development

```bash
# Install dependencies
pnpm install

# Start development server (runs on port 3000)
pnpm dev
# or
pnpm start
```

### Building & Production

```bash
# Build for production (runs vite build && tsc)
pnpm build

# Preview production build
pnpm serve
```

### Testing

```bash
# Run tests with Vitest
pnpm test
```

## 🎨 UI Components (shadcn/ui)

This project uses shadcn/ui components with the "New York" style configuration.

### Adding Components

```bash
# Add individual components
pnpm dlx shadcn@latest add button
pnpm dlx shadcn@latest add card
pnpm dlx shadcn@latest add input

# Or use the shorthand
pnpm ui:add button
```

### Available Components
- Button, Card (already installed)
- [Browse all components](https://ui.shadcn.com/docs/components)

## 🗂️ Project Structure

```
src/
├── components/           # Custom components
│   ├── ui/              # shadcn/ui components
│   │   ├── button.tsx
│   │   └── card.tsx
│   └── Header.tsx       # Custom header component
├── lib/
│   └── utils.ts         # Utility functions (cn helper)
├── routes/              # File-based routing
│   ├── __root.tsx       # Root layout with Header
│   └── index.tsx        # Home page
├── routeTree.gen.ts     # Auto-generated route tree (do not edit)
├── main.tsx             # App entry point
├── styles.css           # Global styles & Tailwind
└── logo.svg
```

## 🛣️ Routing (TanStack Router)

This project uses TanStack Router with file-based routing. Routes are automatically generated based on files in the `src/routes/` directory.

### Adding Routes

Create new route files in the `src/routes/` directory:

```tsx
// src/routes/about.tsx
import { createRoute } from '@tanstack/react-router'
import { rootRoute } from './__root'

export const Route = createRoute({
  getParentRoute: () => rootRoute,
  path: '/about',
  component: () => <div>About Page</div>,
})
```

### Navigation

Use the `Link` component for SPA navigation:

```tsx
import { Link } from "@tanstack/react-router"

<Link to="/about">About</Link>
```

### Layout Structure

The root layout (`src/routes/__root.tsx`) includes:
- Header component with navigation
- `<Outlet />` for route content  
- TanStack Router Devtools (development only)
- TanStack React Devtools

## ⚙️ Configuration

### TypeScript
- Strict mode enabled with ESNext/ES2022 target
- Path aliases: `@/*` maps to `src/*`
- React JSX transform

### Tailwind CSS
- CSS variables enabled
- Base color: zinc
- Custom styles in `src/styles.css`

### shadcn/ui Configuration
- Style: "new-york"
- CSS variables: enabled
- Icon library: Lucide React
- Component aliases configured for easy imports


## 📊 Data Fetching

### Route Loaders
TanStack Router provides built-in data loading with loaders:

```tsx
// src/routes/users.tsx
export const Route = createRoute({
  getParentRoute: () => rootRoute,
  path: '/users',
  loader: async () => {
    const response = await fetch('/api/users')
    return response.json()
  },
  component: () => {
    const users = Route.useLoaderData()
    return (
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    )
  },
})
```

### TanStack Query (Optional)
For more advanced data fetching, add TanStack Query:

```bash
pnpm add @tanstack/react-query @tanstack/react-query-devtools
```

## 🎛️ Available Scripts

| Command | Description |
|---------|-------------|
| `pnpm dev` | Start development server on port 3000 |
| `pnpm start` | Alias for `pnpm dev` |
| `pnpm build` | Build for production (includes TypeScript check) |
| `pnpm serve` | Preview production build |
| `pnpm test` | Run tests with Vitest |
| `pnpm ui:add <component>` | Add shadcn/ui component |

## 🚧 Development Features

- **Hot Module Replacement** with Vite
- **TanStack Router Devtools** for route debugging
- **TanStack React Devtools** for React debugging  
- **TypeScript** strict mode with path aliases
- **Web Vitals** reporting

## 📚 Documentation & Resources

- [TanStack Router Docs](https://tanstack.com/router)
- [shadcn/ui Components](https://ui.shadcn.com/docs/components)
- [Tailwind CSS v4 Docs](https://tailwindcss.com)
- [Vite Documentation](https://vitejs.dev)
- [Vitest Testing Framework](https://vitest.dev)

## 🏗️ Architecture Notes

- **File-based routing** with automatic route tree generation
- **CSS-in-JS** not used - pure Tailwind + CSS variables
- **Component co-location** encouraged
- **TypeScript strict mode** for better DX
- **Modern React patterns** with hooks and functional components
