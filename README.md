# Contentstack Kickstart: Veda - The Revival Collection

**A production-ready Next.js 15 e-commerce template powered by Contentstack**

🎯 **Built for Contentstack Explorer Accounts**: This kickstart is designed to work seamlessly with free Contentstack Explorer accounts, providing all the features you need to build stunning content-driven websites.

[Live Demo](https://kickstart-veda.vercel.app) • [GitHub Repository](https://github.com/contentstack/kickstart-veda)

## About This Project

**Veda: The Revival Collection** showcases an upscale unisex jewelry line with four distinct product collections inspired by early 2000s pop culture. This kickstart demonstrates how to build a modern Next.js application with Contentstack as the headless CMS.

**Important**: This is a **content template**, not a complete e-commerce system. It includes product displays, categories, and rich content pages, but does not include shopping cart, checkout, or payment integration.

### Key Features

- Complete content structure with products, product lines, categories, and dynamic pages
- Visual Builder support with drag-and-drop components
- Real-time Live Preview for content editing
- TypeScript types for all content models
- Next.js 15 App Router with ISR and streaming SSR
- Responsive design with Tailwind CSS 4.x
- Built-in image optimization via Contentstack
- Optimized for Contentstack Explorer (free) accounts

## Architecture Overview

```
kickstart-veda/
├── app/                         # Next.js 15 App Router
│   ├── [[...slug]]/            # Dynamic pages
│   ├── category/[category]/    # Category pages
│   └── products/[line]/        # Product pages
├── components/                  # React components
│   ├── Pages/                  # Page-level components
│   ├── ComponentsRenderer.tsx  # Dynamic component mapper
│   └── [UI Components]         # Hero, List, Media, etc.
└── lib/                        # Utilities & types
    ├── contentstack.ts         # SDK configuration
    ├── types.ts                # TypeScript definitions
    └── pageUtils.ts            # Data fetching
```

## Getting Started

### Prerequisites

- Node.js 20+ and npm
- A Contentstack account ([Sign up for free](https://www.contentstack.com/community))
- Basic knowledge of Next.js and React

### Quick Setup

1. **Install the Contentstack CLI**

```bash
npm install -g @contentstack/cli
```

2. **Set your region** (Explorer accounts use EU)

```bash
csdx config:set:region EU
```

3. **Authenticate**

```bash
csdx auth:login
```

4. **Create your stack** (find your Organization ID under Org admin)

```bash
csdx cm:stacks:seed --repo "contentstack/kickstart-veda-seed" --org "<YOUR_ORG_ID>" -n "Veda: The Revival Collection"
```

5. **Create tokens** in Contentstack dashboard

   - Navigate to Settings → Tokens
   - Create a delivery token with preview token enabled
   - Copy both tokens

6. **Configure environment variables** (create `.env.local`)

These are all delivery related so can be PUBLIC.

```bash
NEXT_PUBLIC_CONTENTSTACK_API_KEY=blt...
NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN=cs...
NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN=cs...
NEXT_PUBLIC_CONTENTSTACK_REGION=EU
NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT=development
NEXT_PUBLIC_CONTENTSTACK_PREVIEW=true
```

**Note**: All variables use `NEXT_PUBLIC_` prefix because they're needed in client-side components for Live Preview functionality.

7. **Enable Live Preview** in Contentstack

   - Go to Settings → Live Preview
   - Set preview URL to `http://localhost:3000`

8. **Install and run**

```bash
npm install
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) to see your site!

## Live Preview & Visual Builder

Contentstack Live Preview enables real-time content editing without page refreshes:

- **CSLP Tags**: Editable fields have `data-cslp` attributes for live editing
- **Real-time Updates**: Changes in Contentstack instantly appear in the preview
- **Visual Builder**: Drag-and-drop interface for adding, reordering, and editing components
- **No Page Reload**: Only changed content updates, maintaining your scroll position

To use: Open any entry in Contentstack → Click Live Preview → Edit and see changes instantly!

## Technical Highlights

- **Dynamic Components**: `ComponentsRenderer` maps Contentstack modular blocks to React components
- **Type-Safe Fetching**: TypeScript interfaces for all content types with React Cache
- **Region-Specific SDK**: Configured for EU region with automatic endpoint resolution
- **CSLP Integration**: Components receive `$` prop with editable tags for Live Preview
- **Catch-All Routing**: `[[...slug]]` handles all dynamic pages with ISR (30-min revalidation)
- **Unified Data Fetching**: `pageUtils.ts` provides consistent data fetching across all page types

## Content Model

### Content Types

- **Page**: Generic pages with modular components
- **Product**: Individual jewelry items with pricing and media
- **Product Line**: Collections (Digital Dawn, Urban Armor, etc.)
- **Category**: Product categories (Earrings, Rings, etc.)
- **Header**: Site navigation

### Modular Blocks

- **Hero**: Full-width banner with media and CTAs
- **List**: Grid of product/category cards
- **Two Column**: Split layout with flexible content
- **Media**: Image or video block
- **Rich Text**: WYSIWYG content

## Styling & Image Optimization

**Tailwind CSS 4.x** with PostCSS plugin architecture provides utility-first styling.

**Image Optimization** uses Contentstack's built-in image delivery system with URL parameters:

- Automatic format selection (WebP/AVIF)
- Responsive sizing on-the-fly
- Global CDN distribution
- No external dependencies needed

Example: `${asset.url}?width=800&auto=webp&quality=80`

## Security & Performance

- **Read-only tokens**: Delivery tokens for published content, preview tokens for drafts
- **Content sanitization**: Rich text sanitized with `isomorphic-dompurify`
- **ISR**: 30-minute revalidation with React Cache
- **Streaming SSR**: Fast TTFB and lazy-loaded images

## Development

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run lint     # Run ESLint
```

The `updateLaunchConfig.mjs` script runs before build to generate `launch.json` with all URLs for optimal CDN caching.

## Key Dependencies

- **Next.js 15** with React 19 and App Router
- **@contentstack/delivery-sdk** & **@contentstack/live-preview-utils**
- **Tailwind CSS 4.x** for styling
- **TypeScript** for type safety

## Use Cases

Perfect for product catalogs, marketing sites, content-heavy projects, POCs, and learning headless CMS architecture.

**Not included**: Shopping cart, checkout, payments, authentication, or order management. For full e-commerce, integrate with Shopify, Stripe, or similar services.

## Contentstack Explorer (Free) Account

This kickstart uses only features available in the free Explorer plan:

- Generous API calls
- Live Preview & Visual Builder
- Multiple environments
- Asset management with CDN
- Additional products: Personalize, Brand Kit, Automate, Launch (free tier), and more

Perfect for learning, prototyping, personal projects, and client demos!

## Contributing

Issues, feature requests, and pull requests are welcome! Check [existing issues](https://github.com/contentstack/kickstart-veda/issues) or join our [Discord community](https://www.contentstack.com/community).

## License

MIT License - see [LICENSE](https://github.com/contentstack/kickstart-veda/blob/main/LICENSE) for details.

## Support

- [Contentstack Documentation](https://www.contentstack.com/docs)
- [Discord Community](https://www.contentstack.com/community)

---

**Built with ❤️ by Contentstack**
