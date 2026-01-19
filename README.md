# Griffin - About Section Component

## Overview

**Griffin** is a minimalist, metrics-focused about section component designed for agency websites, corporate pages, and portfolio "about us" sections. Featuring bold typography, strategic white space, and a clean two-column layout, Griffin effectively communicates brand experience while maintaining visual impact.

<img width="1606" height="876" alt="_C__Users_STUDENT_Desktop_Projects_Granite_index html" src="https://github.com/user-attachments/assets/4001dc3a-2205-4b59-8ec0-ae6371ee90cc" />

## Live Demo

[View Component](https://lefajmofokeng.github.io/Griffin/)

## Technical Architecture

### Core Features
- **Pure HTML/CSS Implementation** - Zero JavaScript dependencies
- **Flexbox Layout System** - Responsive two-column to single-column design
- **Custom SVG Integration** - Inline SVG for iconography without external libraries
- **CSS Custom Properties** - Theming system with semantic color variables
- **Type Scale System** - Hierarchical typography with responsive adjustments

### Design System

#### Typography
- **Primary Font:** Inter (300, 400, 600, 700 weights)
- **Huge Number:** 180px desktop scaling to 100px mobile
- **Body Text:** 29px large copy for emphasis
- **Label Text:** 19px for supporting information
- **Tag Text:** 11px uppercase for categorization

#### Color Palette
```css
--color-primary-text: #000000;    /* Main text color */
--color-accent-red: #ea4335;      /* Brand accent for tags */
--color-secondary: #555555;       /* Supporting text */
```

#### Layout Specifications
- **Container Width:** 1200px maximum with 90% fluid width
- **Column Gap:** 80px desktop, 40px mobile
- **Pill Radius:** 9999px (fully rounded)
- **Vertical Rhythm:** Consistent spacing using flexbox gaps

## Component Structure

```
design-section/
├── content-grid/
│   ├── metric-column/
│   │   ├── tag-pill/
│   │   │   └── tag-icon (SVG)
│   │   ├── huge-number (05)
│   │   └── metric-label
│   └── content-column/
│       └── main-copy/
│           ├── p (paragraph 1)
│           └── p (paragraph 2)
```

## Integration Guide

### Basic Implementation

1. **Include Dependencies:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="griffin.css">
```

2. **HTML Template:**
```html
<section class="design-section">
    <div class="content-grid">
        <div class="metric-column">
            <div class="tag-pill">
                <span class="tag-icon">
                    <!-- Custom SVG icon -->
                </span>
                ABOUT US
            </div>
            <div class="huge-number">05</div>
            <p class="metric-label">Your metric description</p>
        </div>
        <div class="content-column">
            <div class="main-copy">
                <p>First paragraph of your about text.</p>
                <p>Second paragraph or tagline.</p>
            </div>
        </div>
    </div>
</section>
```

## Customization Options

### Theming
```css
:root {
    /* Custom color scheme */
    --color-primary-text: #1a1a1a;
    --color-accent-red: #007acc;
    --color-secondary: #666666;
}

/* Alternative layouts */
.content-grid.alternate {
    flex-direction: row-reverse;
}

.tag-pill.alternate {
    background-color: #000000;
    color: #ffffff;
}
```

### Content Variations
- **Metric Types:** Years, clients, projects, satisfaction rates
- **Icon Options:** Replace SVG with custom icons or emoji
- **Layout Variants:** Reverse columns, vertical stacking, inline metrics
- **Interaction States:** Add hover effects or animation triggers

## Performance Considerations

### Optimization Features
- **Inline SVG:** No external icon requests
- **Efficient Selectors:** Minimal CSS specificity
- **Responsive Images:** Ready for background images if added
- **Critical CSS Friendly:** Small footprint for inlining

### Additional Optimizations
1. **Font Loading Strategy:**
```css
.inter-font {
    font-family: 'Inter', sans-serif;
    font-display: swap;
}
```

2. **Image Optimization:** (if background images are added)
```html
<div class="metric-column" 
     style="background-image: url('optimized-image.webp');">
```

## Browser Compatibility

### Support Matrix
- **Flexbox:** Full support in all modern browsers
- **CSS Variables:** Native support in modern browsers
- **SVG:** Full support with inline implementation
- **Viewport Units:** Partial support with fallbacks

### Fallback Strategy
```css
/* Fallback for older browsers */
.huge-number {
    font-size: 10rem; /* Fallback for vw units */
}

.content-grid {
    display: block; /* Fallback for flexbox */
}

.content-grid::after {
    clear: both;
    content: '';
    display: table;
}
```

## Accessibility Features

### Built-in Accessibility
- **Semantic HTML:** Proper section and paragraph structure
- **Color Contrast:** AAA compliant for all text elements
- **Keyboard Navigation:** Native focus for interactive elements
- **Screen Reader Friendly:** Logical content flow

### Enhanced Accessibility
```html
<section class="design-section" role="region" aria-labelledby="about-heading">
    <div class="content-grid">
        <div class="metric-column" aria-label="Company statistics">
            <div class="tag-pill" role="status">
                <span class="tag-icon" aria-hidden="true">
                    <!-- SVG icon -->
                </span>
                <span class="sr-only">Category: </span>
                ABOUT US
            </div>
            <div class="huge-number" aria-label="5 years">
                <span class="sr-only">5</span>05
            </div>
        </div>
    </div>
</section>
```

## Usage Examples

### CMS Integration
```php
// WordPress with ACF
<div class="design-section">
    <div class="content-grid">
        <div class="metric-column">
            <div class="tag-pill">
                <span class="tag-icon"><?php echo get_field('icon_svg'); ?></span>
                <?php echo get_field('section_tag'); ?>
            </div>
            <div class="huge-number"><?php echo get_field('metric_number'); ?></div>
            <p class="metric-label"><?php echo get_field('metric_description'); ?></p>
        </div>
        <div class="content-column">
            <div class="main-copy">
                <?php echo get_field('about_content'); ?>
            </div>
        </div>
    </div>
</div>
```

### JavaScript Framework
```jsx
// React Component
const GriffinAbout = ({ metric, tag, description, content }) => {
    return (
        <section className="design-section">
            <div className="content-grid">
                <MetricColumn 
                    number={metric.number}
                    tag={tag}
                    description={metric.description}
                />
                <ContentColumn paragraphs={content} />
            </div>
        </section>
    );
};
```

## Development Guidelines

### Code Standards
- Maintain BEM-like naming convention
- Use CSS variables for theming
- Implement mobile-first responsive design
- Include accessibility features
- Document custom properties

### Testing Checklist
- [ ] Responsive behavior (desktop → mobile)
- [ ] Color contrast accessibility
- [ ] Font loading and fallbacks
- [ ] Print styles if applicable
- [ ] Performance metrics

## License & Usage

Griffin is released under the MIT License, allowing free use, modification, and distribution in both personal and commercial projects.

## Support

For implementation questions or customization requests:
- **Documentation:** Refer to inline code comments
- **Examples:** See `/examples` directory
- **Issues:** Report via GitHub repository

---

*Griffin provides a production-ready about section component that balances visual impact with semantic structure, making it suitable for integration into modern web projects.*



