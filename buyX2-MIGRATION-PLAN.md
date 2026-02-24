# buyX2 - Premium E-Commerce Platform Migration Plan

## 📋 Executive Summary

**Current State:**
- Django 6.0.2 with SQLite database
- Basic Bootstrap 5 templates with glassmorphism CSS
- Two user types: User (customer) and Distributor
- Core models: User, Product, Cart, Order, OrderItem, Review

**Target State:**
- Next.js 15/16 with App Router and Server Components
- Two distinct visual themes: Luxury Customer + Enterprise Distributor
- Elite performance (Lighthouse 95+, Core Web Vitals green)
- Modern 2026 e-commerce trends

---

## 🎨 Architecture Overview

### Folder Structure
```
buyX2-next/
├── app/                          # Next.js App Router
│   ├── (customer)/              # Customer-facing routes (grouped layout)
│   │   ├── layout.tsx           # Customer layout with luxury theme
│   │   ├── page.tsx             # Homepage
│   │   ├── products/
│   │   │   ├── page.tsx         # Product listing
│   │   │   └── [slug]/          # Product detail
│   │   ├── cart/
│   │   ├── checkout/
│   │   └── account/
│   ├── (distributor)/           # Distributor routes (grouped layout)
│   │   ├── layout.tsx           # Distributor layout (sidebar + dark theme)
│   │   ├── dashboard/
│   │   ├── products/
│   │   ├── orders/
│   │   └── inventory/
│   ├── api/                     # API routes
│   ├── layout.tsx               # Root layout
│   └── globals.css              # Tailwind + custom styles
├── components/
│   ├── ui/                      # shadcn/ui components
│   ├── customer/                # Customer-specific components
│   │   ├── Navbar.tsx
│   │   ├── Footer.tsx
│   │   ├── ProductCard.tsx
│   │   ├── ProductGallery.tsx
│   │   ├── CartDrawer.tsx
│   │   └── ...
│   └── distributor/             # Distributor-specific components
│       ├── Sidebar.tsx
│       ├── DataTable.tsx
│       ├── StatsCard.tsx
│       └── ...
├── lib/
│   ├── db.ts                    # Database connection (Prisma)
│   ├── auth.ts                  # Authentication utilities
│   └── utils.ts                 # Helper functions
├── hooks/                       # Custom React hooks
├── public/                      # Static assets
├── tailwind.config.ts           # Tailwind configuration
├── next.config.js               # Next.js configuration
└── package.json
```

### Theme Switching Strategy

1. **Route-based**: Customer routes in `(customer/)` group, distributor in `(distributor/)` group
2. **Layout-based**: Each group has its own layout with distinct theme providers
3. **Component-level**: Shared components accept `theme` prop for customization

---

## 🔧 Technical Stack

### Frontend
- **Framework**: Next.js 15 (App Router, Server Components, Partial Prerendering)
- **Styling**: Tailwind CSS v4 + shadcn/ui
- **Animations**: Framer Motion (subtle, performance-optimized)
- **Icons**: Lucide React
- **Forms**: React Hook Form + Zod validation
- **Tables**: TanStack Table

### Backend (Migration Options)
1. **Option A**: Keep Django as REST API + Next.js frontend (recommended)
2. **Option B**: Full migration to Next.js API routes + Prisma ORM

### Performance Targets
- Lighthouse Score: 95+
- Core Web Vitals: All Green
- FCP: < 1.8s
- LCP: < 2.5s
- FID: < 100ms
- CLS: < 0.1

---

## 📝 Implementation Phases

### Phase 1: Project Setup & Configuration
- [ ] Initialize Next.js 15 project with TypeScript
- [ ] Configure Tailwind CSS v4 with custom theme
- [ ] Set up shadcn/ui components
- [ ] Configure fonts (Geist + Inter)

### Phase 2: Database & API Layer
- [ ] Set up Prisma with SQLite (migrate from Django)
- [ ] Create API routes for products, cart, orders
- [ ] Implement authentication (NextAuth.js)

### Phase 3: Customer Theme Development
- [ ] Create customer layout with luxury theme
- [ ] Build homepage with bento grid, hero section
- [ ] Implement product listing with filters
- [ ] Build product detail with gallery/zoom
- [ ] Create cart, checkout, account pages

### Phase 4: Distributor Theme Development
- [ ] Create distributor layout with sidebar
- [ ] Build dashboard with stats/charts
- [ ] Implement inventory management
- [ ] Create order management views

### Phase 5: Performance Optimization
- [ ] Image optimization with Next/Image
- [ ] Implement lazy loading
- [ ] Add loading skeletons
- [ ] Configure caching strategies

### Phase 6: Testing & Deployment
- [ ] Lighthouse audit & optimization
- [ ] Mobile responsiveness testing
- [ ] Deploy to Vercel

---

## 📦 Key Dependencies

```
json
{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "@prisma/client": "^5.22.0",
    "next-auth": "^4.24.0",
    "@tanstack/react-table": "^8.20.0",
    "recharts": "^2.12.0",
    "framer-motion": "^11.0.0",
    "lucide-react": "^0.400.0",
    "zod": "^3.23.0",
    "react-hook-form": "^7.52.0",
    "@hookform/resolvers": "^3.4.0",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.3.0"
  },
  "devDependencies": {
    "typescript": "^5.5.0",
    "@types/node": "^20.14.0",
    "tailwindcss": "^4.0.0",
    "postcss": "^8.4.0",
    "autoprefixer": "^10.4.0",
    "prisma": "^5.22.0",
    "eslint": "^8.57.0",
    "@eslint/js": "^9.0.0"
  }
}
```

---

## 🎯 Success Metrics

| Metric | Target | Current |
|--------|--------|---------|
| Lighthouse Score | 95+ | N/A |
| Page Load Time | < 2s | N/A |
| Mobile Score | 100 | N/A |
| Accessibility | 100 | N/A |
| SEO | 100 | N/A |

---

## 🔄 Migration Steps from Django

1. **Export Data**: Export products, users, orders from Django to JSON
2. **Set Up Prisma**: Define schema matching Django models
3. **Seed Data**: Import exported data to SQLite via Prisma
4. **Build API**: Create Next.js API routes mirroring Django views
5. **Migrate Templates**: Convert Django templates to React components
6. **Implement Auth**: Set up NextAuth with existing user data
7. **Deploy**: Push to Vercel and configure environment

---

*Document Version: 1.0*
*Created: 2026*
*Project: buyX2 Premium E-Commerce Platform*
