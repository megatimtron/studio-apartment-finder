# Design System Components Library
## Reusable UI Components for Building Portfolio

### CSS Custom Properties (Design Tokens)

```css
:root {
  /* Color System */
  --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
  --accent-gradient: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
  --neutral-gradient: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
  
  /* Text Colors */
  --text-primary: #2d3748;
  --text-secondary: #4a5568;
  --text-tertiary: #718096;
  --text-light: #a0aec0;
  
  /* Surface Colors */
  --surface-primary: #ffffff;
  --surface-secondary: #f7fafc;
  --surface-tertiary: #edf2f7;
  
  /* Border Colors */
  --border-light: #e2e8f0;
  --border-medium: #cbd5e0;
  --border-dark: #a0aec0;
  
  /* Shadow System */
  --shadow-soft: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  --shadow-medium: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
  --shadow-large: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  
  /* Spacing System */
  --spacing-xs: 0.25rem;
  --spacing-sm: 0.5rem;
  --spacing-md: 1rem;
  --spacing-lg: 1.5rem;
  --spacing-xl: 2rem;
  --spacing-2xl: 3rem;
  --spacing-3xl: 4rem;
  
  /* Border Radius */
  --radius-sm: 0.25rem;
  --radius-md: 0.5rem;
  --radius-lg: 0.75rem;
  --radius-xl: 1rem;
  --radius-2xl: 1.5rem;
  
  /* Typography */
  --font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  
  /* Transitions */
  --transition-fast: 0.15s ease;
  --transition-normal: 0.3s ease;
  --transition-slow: 0.5s ease;
  --transition-bounce: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
```

### Base Styles

```css
/* Global Base Styles */
* {
  box-sizing: border-box;
}

body {
  font-family: var(--font-family);
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  min-height: 100vh;
  color: var(--text-primary);
  line-height: 1.6;
  margin: 0;
  padding: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Responsive Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

@media (min-width: 768px) {
  .container {
    padding: 0 var(--spacing-lg);
  }
}

/* Responsive Grid */
.grid {
  display: grid;
  gap: var(--spacing-md);
}

.grid-cols-1 { grid-template-columns: repeat(1, 1fr); }
.grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
.grid-cols-3 { grid-template-columns: repeat(3, 1fr); }

@media (min-width: 768px) {
  .md\:grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
  .md\:grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1024px) {
  .lg\:grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
  .lg\:grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
  .lg\:grid-cols-4 { grid-template-columns: repeat(4, 1fr); }
}
```

### Typography System

```css
/* Heading Styles */
.h1, h1 {
  font-size: 2.5rem;
  font-weight: var(--font-weight-bold);
  line-height: 1.2;
  margin: 0 0 var(--spacing-md) 0;
}

.h2, h2 {
  font-size: 2rem;
  font-weight: var(--font-weight-bold);
  line-height: 1.3;
  margin: 0 0 var(--spacing-md) 0;
}

.h3, h3 {
  font-size: 1.5rem;
  font-weight: var(--font-weight-semibold);
  line-height: 1.4;
  margin: 0 0 var(--spacing-sm) 0;
}

.h4, h4 {
  font-size: 1.25rem;
  font-weight: var(--font-weight-semibold);
  line-height: 1.4;
  margin: 0 0 var(--spacing-sm) 0;
}

/* Responsive Typography */
@media (min-width: 768px) {
  .h1, h1 { font-size: 3rem; }
  .h2, h2 { font-size: 2.5rem; }
}

@media (min-width: 1024px) {
  .h1, h1 { font-size: 4rem; }
  .h2, h2 { font-size: 3rem; }
}

/* Gradient Text */
.gradient-text {
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: var(--font-weight-bold);
}

/* Text Utilities */
.text-center { text-align: center; }
.text-left { text-align: left; }
.text-right { text-align: right; }

.text-primary { color: var(--text-primary); }
.text-secondary { color: var(--text-secondary); }
.text-tertiary { color: var(--text-tertiary); }
.text-light { color: var(--text-light); }
```

### Button Components

```css
/* Base Button */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: var(--spacing-sm) var(--spacing-md);
  border: none;
  border-radius: var(--radius-lg);
  font-weight: var(--font-weight-semibold);
  text-decoration: none;
  cursor: pointer;
  transition: all var(--transition-bounce);
  position: relative;
  overflow: hidden;
}

.btn:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.3);
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Primary Button */
.btn-primary {
  background: var(--primary-gradient);
  color: white;
  box-shadow: var(--shadow-soft);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-medium);
}

.btn-primary:active {
  transform: translateY(0);
}

/* Secondary Button */
.btn-secondary {
  background: var(--surface-primary);
  color: var(--text-primary);
  border: 2px solid var(--border-light);
  box-shadow: var(--shadow-soft);
}

.btn-secondary:hover {
  border-color: var(--border-medium);
  transform: translateY(-1px);
  box-shadow: var(--shadow-medium);
}

/* Outline Button */
.btn-outline {
  background: transparent;
  color: var(--text-primary);
  border: 2px solid var(--border-medium);
}

.btn-outline:hover {
  background: var(--surface-secondary);
  border-color: var(--border-dark);
}

/* Button Sizes */
.btn-sm {
  padding: var(--spacing-xs) var(--spacing-sm);
  font-size: 0.875rem;
}

.btn-lg {
  padding: var(--spacing-md) var(--spacing-xl);
  font-size: 1.125rem;
}

/* Icon Buttons */
.btn-icon {
  padding: var(--spacing-sm);
  border-radius: 50%;
  width: 2.5rem;
  height: 2.5rem;
}
```

### Card Components

```css
/* Base Card */
.card {
  background: var(--surface-primary);
  border-radius: var(--radius-2xl);
  box-shadow: var(--shadow-soft);
  overflow: hidden;
  position: relative;
  transition: all var(--transition-bounce);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-large);
}

/* Card Header */
.card-header {
  padding: var(--spacing-lg);
  border-bottom: 1px solid var(--border-light);
}

/* Card Body */
.card-body {
  padding: var(--spacing-lg);
}

/* Card Footer */
.card-footer {
  padding: var(--spacing-lg);
  border-top: 1px solid var(--border-light);
  background: var(--surface-secondary);
}

/* Property Card */
.property-card {
  background: var(--surface-primary);
  border-radius: var(--radius-2xl);
  overflow: hidden;
  box-shadow: var(--shadow-soft);
  transition: all var(--transition-bounce);
  position: relative;
}

.property-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 6px;
  background: var(--primary-gradient);
  opacity: 0;
  transition: opacity var(--transition-normal);
}

.property-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-large);
}

.property-card:hover::before {
  opacity: 1;
}

/* Feature Card */
.feature-card {
  text-align: center;
  padding: var(--spacing-xl);
  background: var(--surface-primary);
  border-radius: var(--radius-2xl);
  box-shadow: var(--shadow-soft);
  transition: all var(--transition-bounce);
}

.feature-card:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-medium);
}
```

### Icon System

```css
/* Feature Icons */
.feature-icon {
  width: 48px;
  height: 48px;
  border-radius: var(--radius-lg);
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--accent-gradient);
  color: white;
  font-size: 1.25rem;
  margin: 0 auto var(--spacing-md);
  transition: all var(--transition-normal);
}

.feature-icon:hover {
  transform: scale(1.1) rotate(5deg);
}

/* Icon Sizes */
.icon-sm { width: 32px; height: 32px; font-size: 1rem; }
.icon-lg { width: 64px; height: 64px; font-size: 1.5rem; }

/* Icon Variants */
.icon-primary { background: var(--primary-gradient); }
.icon-secondary { background: var(--secondary-gradient); }
.icon-accent { background: var(--accent-gradient); }
.icon-neutral { background: var(--neutral-gradient); }
```

### Navigation Components

```css
/* Navigation Bar */
.navbar {
  position: sticky;
  top: 0;
  z-index: 50;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border-light);
  transition: all var(--transition-normal);
}

.navbar-nav {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: var(--spacing-xl);
  padding: var(--spacing-md) 0;
  margin: 0;
  list-style: none;
}

/* Navigation Links */
.nav-link {
  position: relative;
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: var(--font-weight-semibold);
  padding: var(--spacing-sm) 0;
  transition: all var(--transition-bounce);
  overflow: hidden;
}

.nav-link::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background: var(--primary-gradient);
  transition: width var(--transition-normal);
}

.nav-link:hover,
.nav-link.active {
  color: #667eea;
}

.nav-link:hover::before,
.nav-link.active::before {
  width: 100%;
}

/* Breadcrumb */
.breadcrumb {
  display: flex;
  align-items: center;
  gap: var(--spacing-sm);
  margin: var(--spacing-md) 0;
}

.breadcrumb-item {
  color: var(--text-tertiary);
  text-decoration: none;
}

.breadcrumb-item:hover {
  color: var(--text-primary);
}

.breadcrumb-separator {
  color: var(--text-light);
}
```

### Form Components

```css
/* Form Group */
.form-group {
  margin-bottom: var(--spacing-md);
}

/* Label */
.form-label {
  display: block;
  margin-bottom: var(--spacing-xs);
  font-weight: var(--font-weight-semibold);
  color: var(--text-primary);
}

/* Input */
.form-input {
  width: 100%;
  padding: var(--spacing-sm) var(--spacing-md);
  border: 2px solid var(--border-light);
  border-radius: var(--radius-lg);
  font-size: 1rem;
  transition: all var(--transition-normal);
  background: var(--surface-primary);
}

.form-input:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

/* Select */
.form-select {
  width: 100%;
  padding: var(--spacing-sm) var(--spacing-md);
  border: 2px solid var(--border-light);
  border-radius: var(--radius-lg);
  font-size: 1rem;
  background: var(--surface-primary);
  transition: all var(--transition-normal);
}

.form-select:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}

/* Textarea */
.form-textarea {
  width: 100%;
  padding: var(--spacing-sm) var(--spacing-md);
  border: 2px solid var(--border-light);
  border-radius: var(--radius-lg);
  font-size: 1rem;
  resize: vertical;
  min-height: 120px;
  transition: all var(--transition-normal);
  background: var(--surface-primary);
}

.form-textarea:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
}
```

### Table Components

```css
/* Modern Table */
.table-modern {
  width: 100%;
  background: var(--surface-primary);
  border-radius: var(--radius-xl);
  overflow: hidden;
  box-shadow: var(--shadow-soft);
  border-collapse: collapse;
}

.table-modern thead {
  background: var(--primary-gradient);
  color: white;
}

.table-modern th {
  padding: var(--spacing-md) var(--spacing-lg);
  text-align: left;
  font-weight: var(--font-weight-semibold);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-size: 0.875rem;
}

.table-modern td {
  padding: var(--spacing-md) var(--spacing-lg);
  border-bottom: 1px solid var(--border-light);
}

.table-modern tbody tr {
  transition: all var(--transition-fast);
}

.table-modern tbody tr:hover {
  background: var(--surface-secondary);
  transform: scale(1.01);
}

.table-modern tbody tr:last-child td {
  border-bottom: none;
}

/* Responsive Table */
.table-responsive {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}
```

### Animation Classes

```css
/* Fade Animations */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* Animation Classes */
.animate-fade-in {
  animation: fadeIn 0.6s ease-out;
}

.animate-slide-up {
  animation: slideUp 0.8s ease-out;
}

.animate-slide-left {
  animation: slideInLeft 0.8s ease-out;
}

.animate-slide-right {
  animation: slideInRight 0.8s ease-out;
}

/* Staggered Animations */
.animate-delay-100 { animation-delay: 0.1s; }
.animate-delay-200 { animation-delay: 0.2s; }
.animate-delay-300 { animation-delay: 0.3s; }
.animate-delay-400 { animation-delay: 0.4s; }
.animate-delay-500 { animation-delay: 0.5s; }

/* Loading Animation */
@keyframes skeleton-loading {
  0% { background-position: 100% 50%; }
  100% { background-position: -100% 50%; }
}

.loading-skeleton {
  background: linear-gradient(90deg, #f0f0f0 25%, transparent 37%, transparent 63%, #f0f0f0 75%);
  background-size: 400% 100%;
  animation: skeleton-loading 1.4s ease infinite;
}

/* Pulse Animation */
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}
```

### Utility Classes

```css
/* Spacing Utilities */
.m-0 { margin: 0; }
.m-1 { margin: var(--spacing-xs); }
.m-2 { margin: var(--spacing-sm); }
.m-3 { margin: var(--spacing-md); }
.m-4 { margin: var(--spacing-lg); }
.m-5 { margin: var(--spacing-xl); }

.p-0 { padding: 0; }
.p-1 { padding: var(--spacing-xs); }
.p-2 { padding: var(--spacing-sm); }
.p-3 { padding: var(--spacing-md); }
.p-4 { padding: var(--spacing-lg); }
.p-5 { padding: var(--spacing-xl); }

/* Margin/Padding Directions */
.mt-0 { margin-top: 0; }
.mt-1 { margin-top: var(--spacing-xs); }
.mt-2 { margin-top: var(--spacing-sm); }
.mt-3 { margin-top: var(--spacing-md); }
.mt-4 { margin-top: var(--spacing-lg); }
.mt-5 { margin-top: var(--spacing-xl); }

.mb-0 { margin-bottom: 0; }
.mb-1 { margin-bottom: var(--spacing-xs); }
.mb-2 { margin-bottom: var(--spacing-sm); }
.mb-3 { margin-bottom: var(--spacing-md); }
.mb-4 { margin-bottom: var(--spacing-lg); }
.mb-5 { margin-bottom: var(--spacing-xl); }

/* Display Utilities */
.d-none { display: none; }
.d-block { display: block; }
.d-inline { display: inline; }
.d-inline-block { display: inline-block; }
.d-flex { display: flex; }
.d-grid { display: grid; }

/* Flexbox Utilities */
.flex-row { flex-direction: row; }
.flex-col { flex-direction: column; }
.flex-wrap { flex-wrap: wrap; }
.flex-nowrap { flex-wrap: nowrap; }

.justify-start { justify-content: flex-start; }
.justify-center { justify-content: center; }
.justify-end { justify-content: flex-end; }
.justify-between { justify-content: space-between; }
.justify-around { justify-content: space-around; }

.items-start { align-items: flex-start; }
.items-center { align-items: center; }
.items-end { align-items: flex-end; }
.items-stretch { align-items: stretch; }

/* Position Utilities */
.position-relative { position: relative; }
.position-absolute { position: absolute; }
.position-fixed { position: fixed; }
.position-sticky { position: sticky; }

/* Overflow Utilities */
.overflow-hidden { overflow: hidden; }
.overflow-auto { overflow: auto; }
.overflow-scroll { overflow: scroll; }

/* Border Radius Utilities */
.rounded-none { border-radius: 0; }
.rounded-sm { border-radius: var(--radius-sm); }
.rounded { border-radius: var(--radius-md); }
.rounded-lg { border-radius: var(--radius-lg); }
.rounded-xl { border-radius: var(--radius-xl); }
.rounded-2xl { border-radius: var(--radius-2xl); }
.rounded-full { border-radius: 9999px; }

/* Shadow Utilities */
.shadow-soft { box-shadow: var(--shadow-soft); }
.shadow-medium { box-shadow: var(--shadow-medium); }
.shadow-large { box-shadow: var(--shadow-large); }
.shadow-none { box-shadow: none; }

/* Width/Height Utilities */
.w-full { width: 100%; }
.w-auto { width: auto; }
.h-full { height: 100%; }
.h-auto { height: auto; }
.min-h-screen { min-height: 100vh; }
```

### Responsive Design

```css
/* Responsive Breakpoints */
@media (max-width: 639px) {
  .sm\:hidden { display: none; }
  .sm\:block { display: block; }
  .sm\:flex { display: flex; }
}

@media (min-width: 640px) {
  .sm\:text-sm { font-size: 0.875rem; }
  .sm\:text-base { font-size: 1rem; }
  .sm\:text-lg { font-size: 1.125rem; }
}

@media (min-width: 768px) {
  .md\:hidden { display: none; }
  .md\:block { display: block; }
  .md\:flex { display: flex; }
  .md\:grid { display: grid; }
  
  .md\:text-sm { font-size: 0.875rem; }
  .md\:text-base { font-size: 1rem; }
  .md\:text-lg { font-size: 1.125rem; }
  .md\:text-xl { font-size: 1.25rem; }
  .md\:text-2xl { font-size: 1.5rem; }
  .md\:text-3xl { font-size: 1.875rem; }
  .md\:text-4xl { font-size: 2.25rem; }
}

@media (min-width: 1024px) {
  .lg\:hidden { display: none; }
  .lg\:block { display: block; }
  .lg\:flex { display: flex; }
  .lg\:grid { display: grid; }
  
  .lg\:text-sm { font-size: 0.875rem; }
  .lg\:text-base { font-size: 1rem; }
  .lg\:text-lg { font-size: 1.125rem; }
  .lg\:text-xl { font-size: 1.25rem; }
  .lg\:text-2xl { font-size: 1.5rem; }
  .lg\:text-3xl { font-size: 1.875rem; }
  .lg\:text-4xl { font-size: 2.25rem; }
  .lg\:text-5xl { font-size: 3rem; }
  .lg\:text-6xl { font-size: 3.75rem; }
}

@media (min-width: 1280px) {
  .xl\:text-4xl { font-size: 2.25rem; }
  .xl\:text-5xl { font-size: 3rem; }
  .xl\:text-6xl { font-size: 3.75rem; }
  .xl\:text-7xl { font-size: 4.5rem; }
}
```

### Usage Examples

```html
<!-- Hero Section -->
<section class="hero-section">
  <div class="container">
    <h1 class="h1 gradient-text text-center mb-4">
      Building Name
    </h1>
    <p class="text-xl text-center mb-5">
      Your premium living experience
    </p>
    <div class="text-center">
      <button class="btn btn-primary btn-lg">
        Explore Properties
      </button>
    </div>
  </div>
</section>

<!-- Feature Cards -->
<section class="container">
  <div class="grid md:grid-cols-3 gap-6">
    <div class="feature-card animate-fade-in">
      <div class="feature-icon icon-primary">💰</div>
      <h3 class="h3">Best Value</h3>
      <p class="text-secondary">Compare pricing and get the most for your money</p>
    </div>
    <div class="feature-card animate-fade-in animate-delay-200">
      <div class="feature-icon icon-accent">🏊</div>
      <h3 class="h3">Premium Amenities</h3>
      <p class="text-secondary">Luxury pools, fitness centers, and modern spaces</p>
    </div>
    <div class="feature-card animate-fade-in animate-delay-400">
      <div class="feature-icon icon-secondary">🏙️</div>
      <h3 class="h3">Prime Location</h3>
      <p class="text-secondary">Downtown convenience with walkable access</p>
    </div>
  </div>
</section>

<!-- Property Card -->
<div class="property-card">
  <div class="card-header">
    <h3 class="h3">Property Name</h3>
    <p class="text-secondary">Property description</p>
  </div>
  <div class="card-body">
    <div class="grid md:grid-cols-2 gap-4">
      <div>
        <h4 class="h4">Price Range</h4>
        <p class="text-primary">$2,000 - $3,000</p>
      </div>
      <div>
        <h4 class="h4">Availability</h4>
        <p class="text-primary">Currently Available</p>
      </div>
    </div>
  </div>
  <div class="card-footer">
    <button class="btn btn-primary">Learn More</button>
  </div>
</div>
```
