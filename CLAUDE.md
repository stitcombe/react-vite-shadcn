# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Running the application
- `pnpm install` - Install dependencies
- `pnpm start` or `pnpm dev` - Start development server on port 3000
- `pnpm build` - Build for production (runs `vite build && tsc`)
- `pnpm serve` - Preview production build
- `pnpm test` - Run tests with Vitest

### Adding shadcn/ui components
- `pnpm dlx shadcn@latest add <component>` - Add shadcn/ui components (e.g., `pnpm dlx shadcn@latest add button`)
- Use the latest version as specified in .cursorrules

## Architecture Overview

This is a React application built with:
- **Vite** as the build tool and dev server
- **TanStack Router** for file-based routing with auto-generated route tree
- **shadcn/ui** for UI components with Tailwind CSS styling
- **TypeScript** with strict configuration
- **Vitest** for testing with jsdom environment

### Key Architecture Patterns

**Routing Structure:**
- File-based routing in `src/routes/` directory
- `__root.tsx` contains the layout with Header component and devtools
- Route tree is auto-generated in `routeTree.gen.ts`
- Uses TanStack Router with features like preloading, scroll restoration, and structural sharing

**Component Organization:**
- UI components in `src/components/ui/` (shadcn/ui components)
- Custom components in `src/components/`
- Utilities in `src/lib/utils.ts` with cn() function for className merging

**Styling:**
- Tailwind CSS v4 with CSS variables
- shadcn/ui "new-york" style configuration
- Base styles in `src/styles.css`

**Path Aliases:**
- `@/*` maps to `src/*` (configured in both tsconfig.json and vite.config.ts)
- shadcn/ui aliases: `@/components`, `@/lib/utils`, `@/components/ui`, `@/lib`, `@/hooks`

**Development Tools:**
- TanStack Router Devtools integrated
- TanStack React Devtools with bottom-left positioning
- Web vitals reporting available

### File Structure Conventions
- Routes: `src/routes/` (file-based routing)
- Components: `src/components/` and `src/components/ui/`
- Utilities: `src/lib/`
- Styles: `src/styles.css`
- Generated files: `src/routeTree.gen.ts` (auto-generated, do not edit)

## Development Container (Devcontainer)

This repository includes a development container configuration for consistent development environments:

**Container Features:**
- Based on Node.js 22 with pre-installed development tools
- Claude Code CLI pre-installed for AI-assisted development
- Zsh shell with Powerlevel10k theme and useful plugins (git, fzf)
- VS Code extensions: ESLint, Prettier, GitLens
- Persistent bash history and Claude configuration via volumes
- Network capabilities for advanced development scenarios

**Included Tools:**
- Package managers: npm, pnpm (via corepack), yarn (via corepack)
- Development: git, gh (GitHub CLI), less, nano, vim
- Network utilities: iptables, ipset, iproute2, dnsutils
- Other utilities: fzf, jq, git-delta, aggregate

**VS Code Configuration:**
- Format on save enabled with Prettier
- ESLint auto-fix on save
- Zsh as default terminal
- Optimized settings for React/TypeScript development

**Usage:**
- Open in VS Code with Dev Containers extension
- Or use `claude code` from outside the container to leverage the environment
- Container automatically sets up firewall rules and development environment

## TypeScript Configuration
- Uses ESNext modules with bundler resolution
- Strict mode enabled with additional linting rules
- Path mapping configured for `@/*` imports
- Target ES2022 with React JSX transform