# code-storm-ui-
/* NovaUI Framework - Advanced Design System */

/* Custom Properties System with Context Awareness */
:host, :root {
  /* Adaptive Color System with Dynamic Ranges */
  --hue-primary: 240;
  --hue-accent: 330;
  --hue-neutral: 210;
  
  /* Core Colors with Custom Calculations */
  --color-primary: hsl(var(--hue-primary), 75%, 50%);
  --color-primary-surface: hsl(var(--hue-primary), 75%, 95%);
  --color-accent: hsl(var(--hue-accent), 80%, 55%);
  --color-accent-surface: hsl(var(--hue-accent), 80%, 95%);
  --color-neutral: hsl(var(--hue-neutral), 10%, 50%);
  --color-neutral-surface: hsl(var(--hue-neutral), 10%, 95%);
  
  /* System Semantics */
  --surface-main: hsl(var(--hue-neutral), 5%, 99%);
  --surface-raised: hsl(var(--hue-neutral), 5%, 100%);
  --surface-sunken: hsl(var(--hue-neutral), 10%, 97%);
  --surface-emphasis: hsl(var(--hue-neutral), 10%, 93%);
  
  /* Text Colors with Optical Balance */
  --text-primary: hsl(var(--hue-neutral), 15%, 15%);
  --text-secondary: hsl(var(--hue-neutral), 10%, 40%);
  --text-tertiary: hsl(var(--hue-neutral), 5%, 60%);
  --text-inverse: hsl(var(--hue-neutral), 5%, 98%);
  
  /* Viewport Relative Spacing Units */
  --space-unit: clamp(0.25rem, 0.5vw, 0.5rem);
  --space-xs: calc(var(--space-unit) * 1);
  --space-sm: calc(var(--space-unit) * 2);
  --space-md: calc(var(--space-unit) * 3);
  --space-lg: calc(var(--space-unit) * 5);
  --space-xl: calc(var(--space-unit) * 8);
  
  /* Optical Adjustments */
  --border-thin: clamp(1px, 0.1vw, 2px);
  --radius-sm: calc(var(--space-xs) * 1.5);
  --radius-md: calc(var(--space-sm) * 1.5);
  --radius-lg: calc(var(--space-md) * 1.5);
  --radius-pill: 9999px;
  
  /* Elevation System with Real Physics */
  --shadow-depth-1: 0 2px 4px -1px rgba(0,0,0,0.07), 0 1px 2px -1px rgba(0,0,0,0.05);
  --shadow-depth-2: 0 5px 10px -3px rgba(0,0,0,0.08), 0 2px 4px -2px rgba(0,0,0,0.06);
  --shadow-depth-3: 0 15px 25px -5px rgba(0,0,0,0.09), 0 8px 10px -6px rgba(0,0,0,0.08);
  
  /* Motion Expressions */
  --transition-bounce: cubic-bezier(0.2, 1.5, 0.5, 1);
  --transition-smooth: cubic-bezier(0.4, 0.1, 0.3, 1);
  --transition-quick: 160ms;
  --transition-medium: 240ms;
  --transition-slow: 350ms;
}

/* Advanced Reset with Enhanced Accessibility */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  border: 0;
  font-family: inherit;
  scrollbar-width: thin;
  scrollbar-color: var(--color-neutral) transparent;
}

:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}

::selection {
  background: hsl(var(--hue-primary), 70%, 85%);
  color: var(--text-primary);
}

html {
  scroll-behavior: smooth;
  -webkit-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  text-size-adjust: 100%;
}

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
  line-height: 1.5;
  background: var(--surface-main);
  color: var(--text-primary);
  -webkit-font-smoothing: antialiased;
}

/* Contextual Container System */
.nova-container {
  width: 100%;
  max-width: min(90%, 75rem);
  margin-inline: auto;
  padding: var(--space-md);
}

/* Adaptive Flow System */
.nova-flow {
  display: flex;
  flex-direction: column;
  gap: var(--space-md);
}

.nova-flow[data-spacing="compact"] { gap: var(--space-sm); }
.nova-flow[data-spacing="loose"] { gap: var(--space-lg); }
.nova-flow[data-direction="row"] { flex-direction: row; flex-wrap: wrap; }

/* Adaptive Grid with Context Intelligence */
.nova-grid {
  display: grid;
  gap: var(--space-md);
  grid-template-columns: repeat(var(--grid-cols, 1), 1fr);
}

@media (min-width: 640px) {
  .nova-grid { --grid-cols: var(--grid-cols-sm, 2); }
}

@media (min-width: 1024px) {
  .nova-grid { --grid-cols: var(--grid-cols-md, 3); }
}

@media (min-width: 1280px) {
  .nova-grid { --grid-cols: var(--grid-cols-lg, 4); }
}

/* Aspect Ratio Controller */
.nova-aspect {
  position: relative;
  width: 100%;
}

.nova-aspect::before {
  content: "";
  display: block;
  padding-top: calc(var(--aspect-h, 9) / var(--aspect-w, 16) * 100%);
}

.nova-aspect > * {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* Smart Card System */
.nova-card {
  background: var(--surface-raised);
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-depth-1);
  padding: var(--space-md);
  transition: transform var(--transition-medium) var(--transition-smooth),
              box-shadow var(--transition-medium) var(--transition-smooth);
  position: relative;
  isolation: isolate;
  overflow: hidden;
}

.nova-card:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-depth-2);
}

.nova-card::after {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at var(--x, 50%) var(--y, 50%), 
              rgba(255,255,255,0.2) 0%, transparent 50%);
  opacity: 0;
  transition: opacity var(--transition-medium) var(--transition-smooth);
  z-index: -1;
  pointer-events: none;
}

.nova-card:hover::after {
  opacity: 1;
}

/* Tactile Button System */
.nova-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-xs);
  padding: var(--space-sm) var(--space-md);
  background: var(--color-primary);
  color: var(--text-inverse);
  border-radius: var(--radius-sm);
  font-weight: 500;
  cursor: pointer;
  user-select: none;
  position: relative;
  overflow: hidden;
  transition: transform var(--transition-quick) var(--transition-bounce),
              background var(--transition-quick) var(--transition-smooth);
}

.nova-button:active {
  transform: scale(0.97);
}

.nova-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom, rgba(255,255,255,0.1), transparent);
  opacity: 0;
  transition: opacity var(--transition-quick) var(--transition-smooth);
}

.nova-button:hover::before {
  opacity: 1;
}

/* Adaptive Content Reveal System */
.nova-reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity var(--transition-medium) var(--transition-smooth),
              transform var(--transition-medium) var(--transition-smooth);
}

.nova-reveal[data-visible="true"] {
  opacity: 1;
  transform: translateY(0);
}

/* Fluid Typography System */
.nova-text-fluid {
  font-size: clamp(var(--min-size, 1rem), var(--pref-size, 3vw), var(--max-size, 1.5rem));
}

/* State Layer System */
.nova-state-layer {
  position: relative;
  isolation: isolate;
}

.nova-state-layer::before {
  content: '';
  position: absolute;
  inset: 0;
  background-color: currentColor;
  opacity: 0;
  transition: opacity var(--transition-quick);
  z-index: -1;
  border-radius: inherit;
}

.nova-state-layer:hover::before {
  opacity: 0.05;
}

.nova-state-layer:active::before {
  opacity: 0.1;
}

/* Scroll Snap Carousel */
.nova-carousel {
  display: flex;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  gap: var(--space-md);
  padding: var(--space-md);
  scrollbar-width: none;
}

.nova-carousel::-webkit-scrollbar {
  display: none;
}

.nova-carousel > * {
  scroll-snap-align: start;
  flex: 0 0 var(--item-width, 85%);
}

@media (min-width: 768px) {
  .nova-carousel > * {
    flex: 0 0 var(--item-width-md, 45%);
  }
}

@media (min-width: 1024px) {
  .nova-carousel > * {
    flex: 0 0 var(--item-width-lg, 30%);
  }
}

/* Contextual Color Themes */
[data-theme="dark"] {
  --surface-main: hsl(var(--hue-neutral), 15%, 10%);
  --surface-raised: hsl(var(--hue-neutral), 15%, 15%);
  --surface-sunken: hsl(var(--hue-neutral), 15%, 8%);
  --surface-emphasis: hsl(var(--hue-neutral), 15%, 20%);
  
  --text-primary: hsl(var(--hue-neutral), 5%, 90%);
  --text-secondary: hsl(var(--hue-neutral), 5%, 70%);
  --text-tertiary: hsl(var(--hue-neutral), 5%, 50%);
  --text-inverse: hsl(var(--hue-neutral), 15%, 10%);
  
  --shadow-depth-1: 0 2px 4px -1px rgba(0,0,0,0.3), 0 1px 2px -1px rgba(0,0,0,0.2);
  --shadow-depth-2: 0 5px 10px -3px rgba(0,0,0,0.4), 0 2px 4px -2px rgba(0,0,0,0.3);
  --shadow-depth-3: 0 15px 25px -5px rgba(0,0,0,0.5), 0 8px 10px -6px rgba(0,0,0,0.4);
}

/* Dynamic Visual Contrast Mode */
@media (prefers-contrast: more) {
  :root {
    --text-primary: black;
    --text-secondary: hsl(var(--hue-neutral), 15%, 30%);
    --text-tertiary: hsl(var(--hue-neutral), 10%, 40%);
    --surface-main: white;
    --radius-sm: 2px;
    --radius-md: 3px;
    --radius-lg: 4px;
  }
  
  [data-theme="dark"] {
    --text-primary: white;
    --text-secondary: hsl(var(--hue-neutral), 5%, 80%);
    --text-tertiary: hsl(var(--hue-neutral), 5%, 70%);
    --surface-main: black;
  }
}

/* Reduced Motion Consideration */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    transition-duration: 0.01ms !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
  }
}
