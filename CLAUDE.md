# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a WebGL practical course codebase containing multiple learning stages (01_integration through 99_portfolio) focused on building interactive WebGL portfolio sites. The `99_portfolio` folder contains the complete implementation.

## Development Commands

### Running the development server
```bash
cd 99_portfolio  # or any other chapter folder
npm install      # or pnpm install
npm run dev      # starts Vite dev server
```

### Building for production
```bash
npm run build    # builds optimized production bundle
npm run preview  # preview production build locally
```

## Architecture

### Core System Architecture

The project follows a modular WebGL architecture centered around Three.js:

- **bootstrap.js**: Main application orchestrator that initializes all systems in sequence
- **world.js**: Three.js scene management, rendering loop, and WebGL object lifecycle
- **Ob.js**: Base class for all WebGL effects, providing common mesh/shader functionality

### Module Organization

**Component Layer** (`scripts/component/`):
- `loader.js`: Asset loading with progress tracking
- `scroller.js`: Smooth scrolling integration with GSAP ScrollTrigger
- `mouse.js`: Custom cursor and mouse interaction system
- `menu.js`: Navigation menu controls
- `scroll-animation.js`: GSAP ScrollTrigger animation registrations

**GLSL Effects** (`scripts/glsl/`):
- Each effect has its own folder (e.g., `distortion-text/`, `displace-slide/`)
- Structure: `index.js` (extends Ob.js), `vertex.glsl`, `fragment.glsl`
- Effects are auto-loaded based on `data-webgl` attributes in HTML

**Helper Utilities** (`scripts/helper/`):
- `viewport.js`: Responsive canvas sizing and camera management
- `INode.js`: DOM manipulation utilities
- `config.js`: Global configuration constants
- `utils.js`: Performance detection, device detection, math utilities

### Data Flow

1. **Initialization**: bootstrap.js orchestrates startup sequence
2. **Asset Loading**: loader.js processes `data-tex-*` attributes from HTML
3. **WebGL Setup**: world.js creates Three.js scene and effect objects
4. **Page Logic**: Page-specific modules (`page/home.js`, `page/sub.js`) handle interactions
5. **Render Loop**: world.js manages RAF loop, calling render() on all effects

### HTML Integration

WebGL effects are declared in HTML using data attributes:
- `data-webgl="effect-name"`: Specifies which effect to load
- `data-tex-1`, `data-tex-2`, etc.: Asset paths for textures/videos
- `data-page="home"`: Determines which page module to load

### Performance System

- Automatic GPU detection and performance mode adjustment
- Touch device optimization
- Debug mode with lil-gui controls and stats.js (enabled via `enableDebugMode(1)`)

### Key Dependencies

- **Three.js**: WebGL rendering engine
- **GSAP**: Animation library with ScrollTrigger for scroll-based animations
- **Vite**: Build tool with GLSL preprocessing via rollup-plugin-glslify
- **Smooth Scrollbar**: Custom scrolling implementation

### Styling Architecture

SCSS organized into:
- `globals/`: Variables, mixins, functions, media queries
- `pages/`: Page-specific styles
- `parts/`: Component styles (menu, mouse, panels, etc.)
- `vendors/`: Third-party CSS

The path alias `#` maps to `/scripts` for cleaner imports throughout the JavaScript modules.

## Cursor Settings & Documentation

### Available Documentation Sources (As of 2025-08-22)
Cursor's "Indexing & Docs" contains the following indexed documentation:
- **WebGL-work** (25/3/31) - Three.js patterns and modern WebGL workflows
- **React-work** (24/6/28) - React 18+ patterns  
- **Next.js-work** (25/8/22) - Latest Next.js specifications
- **Tailwind CSS-work** (25/8/20) - Modern CSS design patterns
- **Astro-work**, **Angular-work**, **PHP-work**, **WordPress-work**, **Python3-work**, etc.

### SpecStory Configuration
- **Auto Save**: Enabled - AI chat history saved to `./.specstory` directory
- **Derived Rules**: Enabled - Auto-generates project-specific AI rules based on chat/composer history
- **Timezone**: UTC for coordinated development
- **Developer Tools**: Enabled for debugging and state exploration

### Development Approach with Cursor
1. **Use @WebGL-work** for Three.js best practices and modern patterns
2. **Use @Docs** for official library documentation (GSAP, Three.js, etc.)
3. **Use @Web** for latest community tutorials and updates
4. **Leverage derived rules** - Cursor automatically learns project patterns from our development history

### Current Code Assessment
The F-RYM codebase already uses modern patterns:
- ✅ ES6+ imports/exports with named imports from Three.js
- ✅ Modern Three.js patterns (r150+ compatible)
- ✅ EffectComposer for post-processing
- ✅ Modular architecture with path aliases
- ✅ Performance monitoring with Stats.js

### Next Steps for Modernization
- Consider TypeScript integration for better type safety
- Explore latest Three.js features via @WebGL-work
- Optimize performance using modern GPU techniques
- Update GLSL shaders with latest best practices