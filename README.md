# Custom Bootstrap Design System (Variables Only)

A lightweight Bootstrap customization approach using only SCSS variables and mixins - no duplication of Bootstrap code.

## Features

- **Squared Design**: All rounded corners removed via Bootstrap variable overrides
- **Custom Color Palette**: Six vibrant colors integrated into Bootstrap's theme system
- **Lightweight**: Only variables and mixins - Bootstrap code comes from your projects
- **Easy Integration**: Just import variables and mixins, then Bootstrap

## Color Palette

| Color | Hex Code | Usage |
|-------|----------|-------|
| Primary Blue | `#006dcc` | Primary buttons, links |
| Light Blue | `#00A6CE` | Secondary elements, info alerts |
| Success Green | `#77BD43` | Success states, positive actions |
| Warning Yellow | `#FDC800` | Warning messages, caution |
| Danger Red | `#EB1946` | Error states, destructive actions |
| Orange | `#F7971E` | Accent color, highlights |

## Usage Options

### Option 1: Direct CSS Import (HTML Pages)
Use the auto-compiled CSS files for simple HTML pages:

```html
<!-- Production version (compressed) -->
<link href="https://cdn.jsdelivr.net/gh/yourusername/your-repo@main/dist/theme.css" rel="stylesheet">

<!-- OR GitHub Pages -->
<link href="https://yourusername.github.io/your-repo/theme.css" rel="stylesheet">

<!-- Development version (expanded with source maps) -->
<link href="https://cdn.jsdelivr.net/gh/yourusername/your-repo@main/dist/theme-dev.css" rel="stylesheet">
```

### Option 2: SCSS Import (Build Process Projects)
For projects with SCSS compilation:

```bash
npm install bootstrap
```

```scss
// Your main.scss in each project
@import 'path/to/design-system/variables';
@import 'path/to/design-system/mixins';
@import '~bootstrap/scss/bootstrap';

// Your project-specific styles
.your-custom-class {
  @include btn-custom(#F7971E); // Use your custom mixins
}
```

## Auto-Compilation with GitHub Actions

This repository automatically compiles SCSS to CSS on every push using GitHub Actions:

- **Compressed version**: `dist/theme.css` - For production use
- **Development version**: `dist/theme-dev.css` - Expanded with source maps
- **Auto-deployment**: Files are available via GitHub Pages and jsDelivr CDN

The GitHub Action:
1. Installs Bootstrap and Sass
2. Compiles your variables + mixins + Bootstrap into CSS
3. Creates both compressed and expanded versions
4. Deploys to GitHub Pages
5. Commits compiled files back to the repo

### CDN Options

**jsDelivr CDN** (Recommended - faster, global CDN):
```html
<link href="https://cdn.jsdelivr.net/gh/yourusername/repo@main/dist/theme.css" rel="stylesheet">
```

**GitHub Pages**:
```html
<link href="https://yourusername.github.io/repo/theme.css" rel="stylesheet">
```

## File Structure

```
your-design-system/
├── _variables.scss    # Bootstrap variable overrides
├── _mixins.scss       # Custom mixins
└── README.md          # This file
```

## Available Features

### Automatic Color Classes
Your custom colors automatically work with Bootstrap utilities:
```html
<button class="btn btn-orange">Orange Button</button>
<div class="bg-light-blue text-white">Light Blue Background</div>
<p class="text-red">Red Text</p>
```

### Custom Mixins
```scss
.hero-section {
  @include gradient-primary;  // Blue gradient
  @include centered-content(1200px);
}

.feature-card {
  @include card-base;
  @include hover-lift;
}

.custom-button {
  @include btn-custom(#F7971E, white, 15%);
}
```

## Benefits of This Approach

1. **No Code Duplication**: Bootstrap comes from each project's node_modules
2. **Easy Updates**: Update Bootstrap version in each project independently
3. **Lightweight**: Only ~100 lines of variables and mixins
4. **Consistent**: All projects automatically get the same styling
5. **Flexible**: Each project can add its own customizations

## Per-Project Implementation

In each project that uses this design system:

```scss
// src/scss/main.scss
@import 'design-system/variables';  // Your custom variables
@import 'design-system/mixins';     // Your custom mixins
@import '~bootstrap/scss/bootstrap'; // Bootstrap from npm

// Project-specific styles
.project-specific {
  @include btn-custom(#77BD43);
  // Other project styles...
}
```

## Updating the Design System

1. Make changes to `_variables.scss` or `_mixins.scss`
2. Commit and push changes
3. In each project using submodules:
   ```bash
   git submodule update --remote
   ```
4. Rebuild your project's CSS

## Browser Support

Same as Bootstrap 5.3+:
- Chrome >= 60
- Firefox >= 60  
- Safari >= 12
- Edge >= 79

## License

MIT License - feel free to use in personal and commercial projects.
