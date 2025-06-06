# VaporizeTextCycle Component Integration Guide

## Project Setup Complete ✅

This project has been successfully set up with:
- **Next.js 15** with App Router
- **TypeScript** for type safety
- **Tailwind CSS v4** for styling
- **shadcn/ui** structure for component organization

## Component Structure

### Main Component
- **Location**: `src/components/ui/vapour-text-effect.tsx`
- **Export**: `VaporizeTextCycle` (default) and `Component` (named export)
- **Type**: Client-side React component with canvas-based particle animation

### Demo Component
- **Location**: `src/components/demo.tsx`
- **Export**: `DemoOne`
- **Purpose**: Demonstrates the VaporizeTextCycle component

## Component Features

### VaporizeTextCycle Props
```typescript
type VaporizeTextCycleProps = {
  texts: string[];                    // Array of texts to cycle through
  font?: {
    fontFamily?: string;              // Font family (default: "sans-serif")
    fontSize?: string;                // Font size (default: "50px")
    fontWeight?: number;              // Font weight (default: 400)
  };
  color?: string;                     // Text color in rgb format
  spread?: number;                    // Particle spread intensity (0-10)
  density?: number;                   // Particle density (0-10)
  animation?: {
    vaporizeDuration?: number;        // Vaporize animation duration in seconds
    fadeInDuration?: number;          // Fade-in duration in seconds
    waitDuration?: number;            // Wait time between cycles in seconds
  };
  direction?: "left-to-right" | "right-to-left";  // Vaporize direction
  alignment?: "left" | "center" | "right";        // Text alignment
  tag?: Tag;                          // HTML tag for SEO (H1, H2, H3, P)
};
```

### Current Configuration
The demo component is configured with:
- **Texts**: `["21st.dev", "Is", "Cool"]`
- **Font**: Inter, 70px, weight 600
- **Color**: White (`rgb(255,255,255)`)
- **Background**: Black full-screen
- **Animation**: 2s vaporize, 1s fade-in, 0.5s wait
- **Direction**: Left-to-right
- **Alignment**: Center

## Dependencies Installed

### Core Dependencies
- `react` ^19.0.0
- `react-dom` ^19.0.0
- `next` 15.3.3

### Styling Dependencies
- `tailwindcss` ^4
- `@tailwindcss/postcss` ^4

### Utility Dependencies
- `clsx` - For conditional class names
- `tailwind-merge` - For merging Tailwind classes

## File Structure
```
src/
├── app/
│   ├── globals.css          # Tailwind CSS v4 configuration
│   ├── layout.tsx           # Root layout
│   └── page.tsx             # Main page (displays demo)
├── components/
│   ├── ui/
│   │   └── vapour-text-effect.tsx  # Main component
│   └── demo.tsx             # Demo component
└── lib/
    └── utils.ts             # Utility functions (cn helper)
```

## Usage Examples

### Basic Usage
```tsx
import VaporizeTextCycle, { Tag } from "@/components/ui/vapour-text-effect";

export default function MyComponent() {
  return (
    <VaporizeTextCycle
      texts={["Hello", "World", "!"]}
      font={{
        fontFamily: "Inter, sans-serif",
        fontSize: "60px",
        fontWeight: 700
      }}
      color="rgb(255, 255, 255)"
    />
  );
}
```

### Advanced Configuration
```tsx
<VaporizeTextCycle
  texts={["Custom", "Animation", "Effect"]}
  font={{
    fontFamily: "Arial, sans-serif",
    fontSize: "80px",
    fontWeight: 600
  }}
  color="rgb(100, 200, 255)"
  spread={8}
  density={7}
  animation={{
    vaporizeDuration: 3,
    fadeInDuration: 1.5,
    waitDuration: 1
  }}
  direction="right-to-left"
  alignment="left"
  tag={Tag.H1}
/>
```

## Running the Project

### Development Server
```bash
npm run dev
```
Visit `http://localhost:3000` to see the component in action.

### Build for Production
```bash
npm run build
npm start
```

## Component Behavior

1. **Static Phase**: Text is displayed normally
2. **Vaporizing Phase**: Text breaks into particles that disperse
3. **Fade-in Phase**: Next text fades in from particles
4. **Waiting Phase**: Brief pause before next cycle
5. **Repeat**: Cycles through all texts in the array

## Performance Notes

- Uses `requestAnimationFrame` for smooth animations
- Optimized for high DPI displays
- Only animates when component is in viewport
- Automatic cleanup when component unmounts
- Canvas-based rendering for optimal performance

## Browser Compatibility

- Modern browsers with Canvas 2D support
- Intersection Observer API support
- RequestAnimationFrame support

## Customization Tips

1. **Font Loading**: Ensure custom fonts are loaded before component renders
2. **Responsive Design**: Adjust font size based on screen size
3. **Color Schemes**: Use CSS variables for dynamic theming
4. **Performance**: Reduce density for better performance on lower-end devices
5. **Accessibility**: The component includes hidden SEO-friendly text elements

## Troubleshooting

### Text Not Appearing
- Check if fonts are loaded
- Verify color contrast against background
- Ensure container has proper dimensions

### Performance Issues
- Reduce `density` prop value
- Decrease `spread` prop value
- Optimize font loading

### Animation Not Starting
- Component must be in viewport to start
- Check browser console for errors
- Verify all dependencies are installed