# Contentstack Kickstart: Veda - The Revival Collection 💎

<div align="center">

![Veda: The Revival Collection](./public/images/veda.png)

**A production-ready Next.js 15 e-commerce template powered by Contentstack**

> 🎯 **Built for Contentstack Explorer Accounts**: This kickstart is specifically designed to work seamlessly with free Contentstack Explorer accounts, providing all the features you need to build stunning content-driven websites without any limitations.

[![Join us on Discord](https://img.shields.io/badge/Join%20Our%20Discord-7289da.svg?style=flat&logo=discord&logoColor=%23fff)](https://community.contentstack.com)
[![Next.js](https://img.shields.io/badge/Next.js-15.5.4-black?logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?logo=typescript)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-4.x-38bdf8?logo=tailwind-css)](https://tailwindcss.com/)

[Live Demo](https://kickstart-veda.eu-contentstackapps.com/) • [Documentation](#documentation) • [Getting Started](#getting-started)

</div>

---

## 📖 About This Project

**Veda: The Revival Collection** is a fully-functional headless content template showcasing an upscale unisex jewelry line with four distinct product sets inspired by early 2000s pop culture. This kickstart demonstrates how to build a modern, production-ready Next.js application with Contentstack as the headless CMS.

> ⚠️ **Important Note**: This is a **content template**, not a complete e-commerce system. It includes product displays, categories, and rich content pages, but does not include shopping cart functionality, checkout processes, or payment integration. It's designed to showcase how to structure and display product content using Contentstack.

### What Makes This Special

- ✨ **Complete Content Structure**: Products, product lines, categories, and dynamic pages (template only - no cart/checkout)
- 🎨 **Visual Builder Support**: Full integration with Contentstack's Visual Builder
- 🔄 **Live Preview**: Real-time content updates with Contentstack Live Preview
- 🎯 **Type-Safe**: Comprehensive TypeScript types for all content models
- ⚡ **Performance Optimized**: Next.js App Router with streaming SSR and ISR
- 🧩 **Component-Driven**: Modular, reusable components with CSLP (Content Stack Live Preview) support
- 📱 **Responsive Design**: Mobile-first approach with Tailwind CSS 4.x
- 🖼️ **Image Optimization**: Contentstack's built-in image delivery system for responsive images
- 🚀 **Explorer-Ready**: Optimized for Contentstack Explorer (free) accounts

---

## 🏗️ Architecture Overview

This project follows a clean, scalable architecture designed for maintainability and developer experience:

```
kickstart-veda/
├── app/                          # Next.js 15 App Router
│   ├── [[...slug]]/             # Catch-all dynamic pages
│   ├── category/[category]/     # Category pages
│   ├── products/
│   │   ├── [line]/[slug]/       # Individual product pages
│   │   └── [line]/              # Product line pages
│   ├── layout.tsx               # Root layout with metadata
│   └── globals.css              # Global styles
├── components/
│   ├── Atoms/                   # Atomic components (Cta, Title, MediaItem)
│   ├── Cards/                   # Card components for listings
│   ├── Pages/                   # Page-level components
│   │   ├── Page.tsx             # Generic page renderer
│   │   ├── Product.tsx          # Product detail page
│   │   ├── ProductLine.tsx      # Product line page
│   │   ├── Category.tsx         # Category page
│   │   └── Preview.tsx          # Live preview wrapper
│   ├── ComponentsRenderer.tsx   # Dynamic component mapper
│   ├── Hero.tsx                 # Hero banner component
│   ├── List.tsx                 # List/Grid component
│   ├── TwoColumn.tsx            # Two-column layout
│   ├── Media.tsx                # Media component
│   ├── RichText.tsx             # Rich text renderer
│   ├── MegaMenu.tsx             # Navigation menu
│   └── Footer.tsx               # Footer component
└── lib/
    ├── contentstack.ts          # Contentstack SDK configuration
    ├── types.ts                 # TypeScript type definitions
    ├── pageUtils.ts             # Page data fetching utilities
    └── filterSearch.ts          # Search & filter utilities
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js 20+ and npm
- A Contentstack account ([Sign up for free](https://community.contentstack.com/))
- Basic knowledge of Next.js and React

### Step 1: Install the Contentstack CLI

The CLI helps you seed your stack with the content model and sample data:

```bash
npm install -g @contentstack/cli

# or use npx without global install
npx @contentstack/cli
```

#### First-time CLI setup?

Set your region (Free Explorer accounts use the EU region):

```bash
# Check available regions
csdx config:get:region

# Set your region
csdx config:set:region EU
```

> 📝 **Note**: Despite using the EU region, Contentstack's CDN ensures lightning-fast API responses globally.

### Step 2: Authenticate

```bash
csdx auth:login
```

### Step 3: Create Your Stack

Find your Organization ID in your Contentstack dashboard under `Org admin` (e.g., `blt481c598b0d8352d9`), then run:

```bash
csdx cm:stacks:seed --repo "contentstack/kickstart-veda-seed" --org "<YOUR_ORG_ID>" -n "Veda: The Revival Collection"
```

This command will:

- Create a new stack in your organization
- Set up all content types (Page, Product, Product Line, Category, Header)
- Import sample content and assets
- Configure taxonomies and relationships

### Step 4: Create a Delivery Token

1. Navigate to `Settings > Tokens` in your Contentstack dashboard
2. Click **+ Add token**
3. Name it (e.g., "Development Token")
4. Select the `development` scope
5. Enable **Create preview token**
6. Save and copy both tokens

### Step 5: Configure Environment Variables

Create a `.env.local` file in the project root:

```bash
# Required: Your stack credentials
NEXT_PUBLIC_CONTENTSTACK_API_KEY=blt...
NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN=cs...
NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN=cs...
NEXT_PUBLIC_CONTENTSTACK_REGION=EU
NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT=development

# Enable Live Preview
NEXT_PUBLIC_CONTENTSTACK_PREVIEW=true

# Optional: Custom endpoints (usually not needed)
# NEXT_PUBLIC_CONTENTSTACK_CONTENT_DELIVERY=
# NEXT_PUBLIC_CONTENTSTACK_PREVIEW_HOST=
# NEXT_PUBLIC_CONTENTSTACK_CONTENT_APPLICATION=
# NEXT_PUBLIC_CONTENTSTACK_IMAGE_HOSTNAME=
```

> 💡 **Tip**: You can find all these values under `Settings > Tokens > [Your Token]`

### Step 6: Enable Live Preview

1. Go to `Settings > Live Preview` in your Contentstack dashboard
2. Click **Enable**
3. Select the `development` environment
4. Set the preview URL: `http://localhost:3000` (or your deployment URL for production)
5. Save the configuration

### Step 7: Install Dependencies & Run

```bash
npm install
npm run dev
```

Your site will be available at [http://localhost:3000](http://localhost:3000) 🎉

### Step 8: Experience Live Preview

1. Open your Contentstack dashboard
2. Navigate to `Entries > Page` (or any content type)
3. Select an entry
4. Click the **Live Preview** icon in the sidebar
5. Edit content and see changes in real-time!

You can also use the **Visual Builder** to drag and drop components visually.

---

## 🔍 Understanding Live Preview

Contentstack Live Preview is a powerful feature that bridges your CMS and your application, enabling real-time content editing without page refreshes. Here's how it works:

### How Live Preview Works

1. **SDK Integration**: The `@contentstack/live-preview-utils` package establishes a communication channel between the Contentstack UI and your application.

2. **CSLP (Content Stack Live Preview) Tags**: Every editable field receives a unique `data-cslp` attribute that identifies it to the Live Preview system.

```typescript
// lib/contentstack.ts
export function initLivePreview() {
  ContentstackLivePreview.init({
    ssr: false,
    enable: process.env.NEXT_PUBLIC_CONTENTSTACK_PREVIEW === "true",
    mode: "builder", // Enables Visual Builder
    stackSdk: stack.config as IStackSdk,
    stackDetails: {
      apiKey: process.env.NEXT_PUBLIC_CONTENTSTACK_API_KEY as string,
      environment: process.env.NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT as string,
    },
    clientUrlParams: {
      host:
        process.env.NEXT_PUBLIC_CONTENTSTACK_CONTENT_APPLICATION ||
        endpoints.application,
    },
    editButton: {
      enable: true,
      exclude: ["outsideLivePreviewPortal"],
    },
  });
}
```

3. **Editable Tags**: When fetching content, editable tags are automatically added in preview mode:

```typescript
if (isPreview) {
  contentstack.Utils.addEditableTags(entry, "page", true);
}
```

4. **Real-time Updates**: When you edit a field in Contentstack, the Live Preview system:
   - Detects the change via the `data-cslp` attribute
   - Fetches the updated content from the Preview API
   - Updates only the changed field in your browser (no full page reload)

### Visual Builder

The Visual Builder mode (`mode: "builder"`) enables drag-and-drop functionality:

- **Add Components**: Click the "+" button to add new modular blocks
- **Reorder Components**: Drag components to rearrange them
- **Delete Components**: Remove unwanted sections
- **Edit In-Place**: Click any text or image to edit directly

All changes are reflected instantly in the preview pane while you work.

---

## 🧩 Key Features & Implementation

### 1. Dynamic Component Rendering

The `ComponentsRenderer` dynamically maps Contentstack components to React components:

```tsx
// components/ComponentsRenderer.tsx
const componentMap = {
  hero: HeroComponent,
  list: ListComponent,
  two_column: TwoColumnComponent,
  media: MediaComponent,
  rich_text: RichTextComponent,
} as const;

export const ComponentsRenderer: React.FC<ComponentsRendererProps> = ({
  components,
  cslp,
  cslpWrapper,
}) => {
  const mappedComponents = mapComponentsToKV(components);

  const renderComponent = (component: any, index: number) => {
    const Component = componentMap[component.name];
    const element = <Component {...component.props} key={key} />;

    // Wrap with CSLP attributes for Live Preview editing
    return isPreview && cslp?.[`${cslpWrapper}__${index}`] ? (
      <div {...cslp?.[`${cslpWrapper}__${index}`]} key={key}>
        {element}
      </div>
    ) : (
      element
    );
  };

  return <>{mappedComponents.map(renderComponent)}</>;
};
```

This approach allows content editors to add, remove, and reorder components without code changes.

### 2. Contentstack SDK Configuration

The SDK is configured with region-specific endpoints and Live Preview support:

```typescript
// lib/contentstack.ts
const region = getRegionForString(process.env.NEXT_PUBLIC_CONTENTSTACK_REGION);
const endpoints = getContentstackEndpoints(region, true);

export const stack = contentstack.stack({
  apiKey: process.env.NEXT_PUBLIC_CONTENTSTACK_API_KEY as string,
  deliveryToken: process.env.NEXT_PUBLIC_CONTENTSTACK_DELIVERY_TOKEN as string,
  environment: process.env.NEXT_PUBLIC_CONTENTSTACK_ENVIRONMENT as string,
  region: region,
  host: endpoints?.contentDelivery,

  live_preview: {
    enable: process.env.NEXT_PUBLIC_CONTENTSTACK_PREVIEW === "true",
    preview_token: process.env.NEXT_PUBLIC_CONTENTSTACK_PREVIEW_TOKEN,
    host: endpoints?.preview,
  },
});
```

### 3. Type-Safe Content Fetching

All content types have TypeScript interfaces and cached fetch functions:

```typescript
// lib/contentstack.ts
export async function getPage(url: string): Promise<Page> {
  const result = await stack
    .contentType("page")
    .entry()
    .addParams({ include_all: true, include_all_depth: 2 })
    .query()
    .where("url", QueryOperation.EQUALS, url)
    .find<Page>();

  if (result.entries) {
    const entry = result.entries[0];

    // Add editable tags for Live Preview
    if (isPreview) {
      contentstack.Utils.addEditableTags(entry, "page", true);
    }

    return entry;
  }

  throw new Error(`Page not found for url: ${url}`);
}

// Cached version for performance
export const getPageCached = cache(getPage);
```

### 4. Unified Routing & Data Fetching

The `pageUtils.ts` file provides unified utilities for all content types:

```typescript
// lib/pageUtils.ts
export function buildPath(
  type: "page" | "category" | "product" | "productLine",
  params: any
): string {
  switch (type) {
    case "page":
      return params.slug ? `/${params.slug.join("/")}` : "/";
    case "category":
      return `/category/${params.category}`;
    case "product":
      return `/products/${params.line}/${params.slug}`;
    case "productLine":
      return `/products/${params.line}`;
  }
}

export async function fetchPageData(params: { slug?: string[] }) {
  const path = buildPath("page", params);
  const header = await getHeaderCached();
  const content = await getPageCached(path);

  return {
    content,
    header,
    path,
    isPreview,
    previewType: "page" as const,
  };
}
```

### 5. Hero Component with CSLP Support

Components receive CSLP attributes via the `$` prop for Live Preview integration:

```tsx
// components/Hero.tsx
export default function Hero({
  description,
  design,
  image,
  title,
  video,
  ctas,
  $, // CSLP attributes for live editing
}: HeroProps) {
  return (
    <div className="md:aspect-[1440/635] relative w-full overflow-hidden">
      {image?.url && (
        <MediaItem
          {...($ && $.image)} // Attach CSLP to make image editable
          src={image.url}
          width={1440}
          height={635}
          alt={title || image.title || ""}
        />
      )}

      <article>
        <Title
          $={$ && $.title} // Attach CSLP to make title editable
          text={title}
        />
        <p {...($ && $.description)}>{description}</p>
      </article>
    </div>
  );
}
```

### 6. Catch-All Routing

The `[[...slug]]` route handles all dynamic pages:

```tsx
// app/[[...slug]]/page.tsx
export default async function SlugPage({ params }: SlugPageProps) {
  const {
    content: page,
    header,
    path,
    isPreview,
    previewType,
  } = await fetchPageData(await params);

  if (isPreview) {
    return <Preview path={path} header={header} type={previewType} />;
  }

  return <Page page={page} header={header} />;
}

// Enable ISR with 30-minute revalidation
export const revalidate = 1800;
export const dynamic = "force-static";
```

---

## 📚 Content Model

### Content Types

| Content Type     | Purpose                                    | Key Fields                                                                        |
| ---------------- | ------------------------------------------ | --------------------------------------------------------------------------------- |
| **Page**         | Generic pages (homepage, about, etc.)      | `url`, `title`, `description`, `components[]`                                     |
| **Product**      | Individual jewelry items                   | `title`, `url`, `price`, `description`, `media[]`, `product_line[]`, `category[]` |
| **Product Line** | Collections (e.g., "Digital Dawn")         | `title`, `url`, `description`, `image`, `products[]`                              |
| **Category**     | Product categories (Earrings, Rings, etc.) | `title`, `url`, `description`, `media`, `products[]`                              |
| **Header**       | Site navigation                            | `logo`, `links[]`                                                                 |

### Modular Blocks

Pages and PDPs use modular blocks for flexible layouts:

- **Hero**: Full-width banner with image/video, title, description, and CTAs
- **List**: Grid of cards (products, categories, or static cards)
- **Two Column**: Split layout with media, rich text, or lists on each side
- **Media**: Standalone image or video block
- **Rich Text**: WYSIWYG content with embedded assets

### Taxonomies

Products are organized using Contentstack's taxonomy feature:

- **Product Line**: Digital Dawn, Urban Armor, Charmed Revival, Elegant Rebellion
- **Category**: Earrings, Necklaces, Bracelets, Rings

---

## 🎨 Styling & Theming

This project uses **Tailwind CSS 4.x** with the new PostCSS plugin architecture:

```js
// postcss.config.mjs
export default {
  plugins: {
    "@tailwindcss/postcss": {},
  },
};
```

### Custom Styles

Global styles are defined in `app/globals.css`:

```css
@import "tailwindcss";

:root {
  --font-inter: "Inter", sans-serif;
}

/* Custom utilities for text shadow */
.text-shadow-sm {
  text-shadow: 0 1px 2px rgb(0 0 0 / 0.5);
}
```

---

## 🖼️ Image Optimization

Images are optimized using **Contentstack's built-in image delivery system**, which provides a powerful transformation API directly from your assets.

### How It Works

Contentstack automatically serves optimized images from your Digital Asset Management (DAM) system using URL parameters:

```tsx
// Example: Contentstack image transformation
const imageUrl = `${asset.url}?width=800&height=600&format=webp&quality=80`;
```

### Transformation Parameters

Contentstack supports various image transformations:

```tsx
// Responsive image with multiple sizes
const srcset = [400, 800, 1200]
  .map((width) => `${asset.url}?width=${width}&auto=webp ${width}w`)
  .join(", ");
```

### Benefits of Contentstack Image Delivery

- **Automatic Format Selection**: Serves WebP or AVIF based on browser support when using `auto=webp`
- **Responsive Sizing**: Generate multiple image sizes on-the-fly with the `width` parameter
- **Quality Control**: Adjust image quality with the `quality` parameter (1-100)
- **Cropping & Fitting**: Use `fit`, `crop`, and `focal_point` for precise control
- **CDN Distribution**: All images served through Contentstack's global CDN
- **No External Dependencies**: No need for third-party services like Cloudinary
- **Lazy Loading**: Implemented with native browser `loading="lazy"` attribute
- **Eager Loading**: Priority images use `loading="eager"` and `fetchPriority="high"`

### Common Transformations

```tsx
// Crop to specific dimensions
`${asset.url}?width=800&height=600&fit=crop` // Maintain aspect ratio
`${asset.url}?width=800&fit=bounds` // Compress for performance
`${asset.url}?quality=80&auto=webp` // Smart crop with focal point
`${asset.url}?width=800&height=600&crop=focalpoint&fp-x=0.5&fp-y=0.5`;
```

This approach keeps everything within the Contentstack ecosystem, perfect for Explorer accounts!

---

## 🔒 Security & Best Practices

### Environment Variables

All sensitive credentials use the `NEXT_PUBLIC_` prefix for client-side access while maintaining security through Contentstack's token scopes:

- **Delivery Tokens**: Read-only access to published content
- **Preview Tokens**: Read access to draft content (only enabled in preview mode)

### Content Security

- Sanitized rich text rendering with `isomorphic-dompurify`
- Type-safe content models prevent injection attacks
- Server-side data fetching prevents exposure of sensitive data

### Performance

- **ISR (Incremental Static Regeneration)**: Pages revalidate every 30 minutes
- **React Cache**: Prevents duplicate API calls during SSR
- **Streaming SSR**: Fast Time to First Byte (TTFB)
- **Image Optimization**: Lazy loading and responsive sizes

---

## 🧪 Development Workflow

### Local Development

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
```

### Pre-build Hook: Cache Priming

The `updateLaunchConfig.mjs` script automatically generates a `launch.json` file for Contentstack Launch deployments. This script runs before each build to optimize performance:

**What it does:**

- Connects to your Contentstack stack
- Fetches all URLs from your content (pages, products, categories, product lines)
- Generates a `launch.json` file with cache priming configuration
- Ensures all pages are pre-built and cached during deployment

**Why it matters:**

- Improves first-visit performance for users
- Prevents cold-start delays on initial page requests
- Optimizes CDN distribution across edge locations
- Makes your site instantly fast on Contentstack Launch

```json
// package.json
{
  "scripts": {
    "prebuild": "npm run update-launch-config"
  }
}
```

The script runs automatically during `npm run build`, but you can also run it manually:

```bash
node updateLaunchConfig.mjs
```

### Live Preview Testing

1. Start the dev server: `npm run dev`
2. Open Contentstack dashboard
3. Navigate to any entry
4. Click **Live Preview** to see real-time updates
5. Use **Visual Builder** to drag and drop components

---

## 📦 Key Dependencies

| Package                              | Version | Purpose                         |
| ------------------------------------ | ------- | ------------------------------- |
| `next`                               | 15.5.4  | React framework with App Router |
| `react`                              | 19.1.1  | UI library                      |
| `@contentstack/delivery-sdk`         | 4.10.0  | Content delivery API client     |
| `@contentstack/live-preview-utils`   | 4.0.2   | Live Preview integration        |
| `@timbenniks/contentstack-endpoints` | 1.0.16  | Region endpoint resolver        |
| `tailwindcss`                        | 4.x     | Utility-first CSS framework     |
| `lucide-react`                       | 0.544.0 | Icon library                    |
| `isomorphic-dompurify`               | 2.28.0  | HTML sanitization               |
| `tailwind-merge`                     | 3.3.1   | Tailwind class merging utility  |

---

## 🎯 Use Cases

This kickstart is perfect for:

- 🛍️ **Product Catalogs**: Display products, collections, and categories (front-end only, no transactions)
- 📄 **Marketing Websites**: Dynamic landing pages with modular components
- 📰 **Content-Heavy Sites**: Blogs, news sites, or documentation
- 🎨 **Design Systems**: Showcase component libraries
- 🚀 **POCs & MVPs**: Rapid prototyping with visual editing
- 🎓 **Learning Projects**: Understand headless CMS architecture with real-world examples
- 🏢 **Agency Presentations**: Demonstrate Contentstack capabilities to clients

### What This Is NOT

This template does **not** include:

- ❌ Shopping cart functionality
- ❌ User authentication/accounts
- ❌ Checkout process
- ❌ Payment processing
- ❌ Order management
- ❌ Inventory tracking

To build a complete e-commerce solution, you would need to integrate services like:

- **Shopify** (headless commerce)
- **Stripe** (payments)
- **Auth0** (authentication)
- **Algolia** (search)

---

## 🆓 Contentstack Explorer Account Features

This kickstart is specifically designed to work seamlessly with **Contentstack Explorer** (free) accounts. All features demonstrated here are available in the Explorer plan:

### Explorer Account Includes

#### Core CMS Features

- ✅ **Big amount of API Calls**: No real restrictions on content delivery, unless you hyper scale
- ✅ **Live Preview**: Real-time content editing and preview
- ✅ **Visual Builder**: Drag-and-drop page building
- ✅ **Content Types**: All the content models used in this project
- ✅ **Modular Blocks**: Build flexible page layouts
- ✅ **Taxonomies**: Organize content with categories and tags
- ✅ **Assets & DAM**: Store and optimize images
- ✅ **Multiple Environments**: Development, staging, production
- ✅ **Webhooks**: Trigger builds on content changes
- ✅ **Content Delivery API**: Fast, global CDN delivery

#### Additional Contentstack Products

- ✅ **Personalize**: Create personalized experiences for different audiences
- ✅ **Brand Kit**: Maintain brand consistency across all content
- ✅ **Developer Hub**: Access to SDKs, APIs, and developer resources
- ✅ **Marketplace**: Browse and install extensions and integrations
- ✅ **Automate**: Workflow automation and content orchestration
- ✅ **Data & Insights**: Analytics and content performance metrics
- ✅ **Launch**: Free hosting tier with automatic deployments

### Perfect for:

- 🎓 **Learning**: Explore headless CMS concepts
- 🚀 **Prototyping**: Build MVPs without cost
- 👨‍💻 **Personal Projects**: Side projects and portfolios
- 📊 **Client Demos**: Showcase capabilities to potential clients
- 🧪 **Experimentation**: Test new ideas and architectures

But for most kickstart projects, the Explorer account has everything you need!

---

## 🤝 Contributing

This is a kickstart project maintained by Contentstack. For issues or feature requests, please:

1. Check existing issues on GitHub
2. Join our [Discord community](https://community.contentstack.com)
3. Submit a pull request with clear description

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 📞 Support

- 📖 [Contentstack Documentation](https://www.contentstack.com/docs)
- 💬 [Discord Community](https://community.contentstack.com)

---
