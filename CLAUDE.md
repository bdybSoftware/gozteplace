# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## IMPORTANT: File Modification Policy

**NEVER EDIT OR MODIFY `original.js`** - This file serves as the reference implementation and base for our forked userscript. All new functionality should be added to separate files that extend or fork the original functionality.

**Active Development File: `gozteplace.js`** - This is our main development file that starts as a copy of `original.js` with added functionality and improvements.

## Project Overview

This is a UserScript (Tampermonkey/Greasemonkey) project called "Wplace Overlay Pro" that provides overlay functionality for wplace.live. The entire codebase is contained in a single compiled JavaScript file (`original.js`) that includes all modules bundled together.

## Architecture

The userscript follows a modular architecture with clear separation of concerns:

### Core Modules (src/core/)
- **gm.ts**: GreaseMonkey API wrappers (`gmGet`, `gmSet`, `gmFetchBlob`) for cross-platform userscript compatibility
- **palette.ts**: Color palette management and color matching functionality
- **store.ts**: Configuration management with localStorage persistence (`loadConfig`, `saveConfig`)
- **canvas.ts**: Canvas operations and image manipulation utilities
- **constants.ts**: Application constants and configuration defaults
- **cache.ts**: LRU cache implementation for performance optimization
- **toast.ts**: Toast notification system
- **overlay.ts**: Core overlay rendering and management logic
- **events.ts**: Event handling and DOM manipulation
- **hook.ts**: Integration hooks with the host website
- **util.ts**: General utility functions

### UI Modules (src/ui/)
- **styles.ts**: CSS styling injected into the page
- **ccModal.ts**: Color correction modal interface
- **rsModal.ts**: Resize modal interface  
- **panel.ts**: Main control panel UI

### Application Entry Points
- **app.ts**: Main application bootstrap (`bootstrapApp`, `applyTemplateFromUrl`)
- **main.ts**: Entry point that initializes the application on window load

## Key Components

### Configuration System
- Uses GreaseMonkey storage APIs for persistence
- Supports themes (dark/light mode)
- Manages overlay collections with import/export functionality

### Overlay Management
- Supports multiple overlays with individual opacity and positioning
- Handles both local files and remote URLs
- Includes template loading from URL parameters
- Canvas-based rendering system

### UI System
- Modal-based interface with draggable panels
- Toast notification system
- Theme-aware styling
- Responsive design for overlay controls

## Development Notes

This is a compiled userscript - the source appears to be TypeScript that has been bundled into a single JavaScript file. The original source structure is preserved in comments throughout the compiled code.

### File Structure
- The single `original.js` file contains the entire application
- No build system is present in this directory
- Source modules are indicated by `// src/module/file.ts` comments

### Key Functions
- `bootstrapApp()`: Main initialization function
- `loadConfig()`/`saveConfig()`: Configuration persistence
- `displayImageFromData()`: Overlay rendering
- `createUI()`: UI initialization
- `applyTemplateFromUrl()`: Template loading from URL parameters

The userscript integrates with wplace.live by injecting UI elements and hooking into the site's canvas rendering system.