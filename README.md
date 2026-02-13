# Magic Portfolio

Magic Portfolio is a simple, clean, beginner-friendly portfolio template. It supports an MDX-based content system for projects and blog posts, an about / CV page and a gallery.

View the demo [here](https://demo.magic-portfolio.com).

![Magic Portfolio](public/images/og/home.jpg)

## Getting started

**1. Clone the repository**
```
git clone https://github.com/once-ui-system/magic-portfolio.git
```

**2. Install dependencies**
```
npm install
```

**3. Run dev server**
```
npm run dev
```

**4. Edit config**
```
src/resources/once-ui.config.js
```

**5. Edit content**
```
src/resources/content.js
```

**6. Create blog posts / projects**
```
Add a new .mdx file to src/app/blog/posts or src/app/work/projects
```

Magic Portfolio was built with [Once UI](https://once-ui.com) for [Next.js](https://nextjs.org). It requires Node.js v18.17+.

## Page structure

Magic Portfolio uses the [Next.js App Router](https://nextjs.org/docs/app). Each route maps to a folder inside `src/app/`, and the page displayed for that route is defined by the `page.tsx` file in the folder.

```
src/app/
├── layout.tsx                  # Root layout (header, footer, route guard, global styles)
├── page.tsx                    # Home page (/)
├── not-found.tsx               # 404 page
├── about/
│   └── page.tsx                # /about
├── work/
│   ├── page.tsx                # /work (project listing)
│   ├── [slug]/
│   │   └── page.tsx            # /work/:slug (individual project)
│   └── projects/               # MDX files for project content
├── blog/
│   ├── page.tsx                # /blog (blog listing)
│   ├── [slug]/
│   │   └── page.tsx            # /blog/:slug (individual blog post)
│   └── posts/                  # MDX files for blog post content
├── gallery/
│   └── page.tsx                # /gallery
├── robots.ts                   # robots.txt generation
├── sitemap.ts                  # sitemap.xml generation
└── api/                        # API routes (authentication, RSS, OG images)
```

### Route configuration

Routes are enabled or disabled in `src/resources/once-ui.config.ts` through the `routes` object:

```ts
const routes: RoutesConfig = {
  "/":        true,
  "/about":   true,
  "/work":    true,
  "/blog":    true,
  "/gallery": true,
};
```

Setting a route to `false` hides it from the navigation header and renders a 404 when visited. The `RouteGuard` component in `src/components/RouteGuard.tsx` enforces this at runtime.

### Password-protected routes

Individual routes can be password-protected via the `protectedRoutes` object in the same config file. The password is set through an environment variable (see `.env.example`). Authentication is handled by the `/api/authenticate` and `/api/check-auth` API routes.

### Dynamic routes

Blog posts and work projects use [dynamic segments](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes) (`[slug]`). Each MDX file placed in `src/app/blog/posts/` or `src/app/work/projects/` automatically becomes a page. The slug is derived from the MDX filename, and `generateStaticParams()` in each dynamic page file pre-renders all slugs at build time.

### Content and metadata

Page content—titles, descriptions, bios, social links, and more—is centralized in `src/resources/content.tsx`. Every page imports from this file, so most text changes only require editing a single place.

## Documentation

Docs available at: [docs.once-ui.com](https://docs.once-ui.com/docs/magic-portfolio/quick-start)

## Features

### Once UI
- All tokens, components & features of [Once UI](https://once-ui.com)

### SEO
- Automatic open-graph and X image generation with next/og
- Automatic schema and metadata generation based on the content file

### Design
- Responsive layout optimized for all screen sizes
- Timeless design without heavy animations and motion
- Endless customization options through [data attributes](https://once-ui.com/docs/theming)

### Content
- Render sections conditionally based on the content file
- Enable or disable pages for blog, work, gallery and about / CV
- Generate and display social links automatically
- Set up password protection for URLs

### Localization
- A localized, earlier version of Magic Portfolio is available with the next-intl library
- To use localization, switch to the 'i18n' branch

## Creators

Lorant One: [Threads](https://www.threads.net/@lorant.one) / [LinkedIn](https://www.linkedin.com/in/lorant-one/)

## Get involved

- Join the Design Engineers Club on [Discord](https://discord.com/invite/5EyAQ4eNdS) and share your project with us!
- Deployed your docs? Share it on the [Once UI Hub](https://once-ui.com/hub) too! We feature our favorite apps on our landing page.

## License

Distributed under the CC BY-NC 4.0 License.
- Attribution is required.
- Commercial usage is not allowed.
- You can extend the license to [Dopler CC](https://dopler.app/license) by purchasing a [Once UI Pro](https://once-ui.com/pricing) license.

See `LICENSE.txt` for more information.

## Deploy with Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fonce-ui-system%2Fmagic-portfolio&project-name=portfolio&repository-name=portfolio&redirect-url=https%3A%2F%2Fgithub.com%2Fonce-ui-system%2Fmagic-portfolio&demo-title=Magic%20Portfolio&demo-description=Showcase%20your%20designers%20or%20developer%20portfolio&demo-url=https%3A%2F%2Fdemo.magic-portfolio.com&demo-image=%2F%2Fraw.githubusercontent.com%2Fonce-ui-system%2Fmagic-portfolio%2Fmain%2Fpublic%2Fimages%2Fog%2Fhome.jpg)