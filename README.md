# React 19 & 19.2 Features Showcase

A comprehensive learning project demonstrating all major features introduced in React 19.0 and React 19.2, with hands-on examples and implementation guides built with **Next.js 15+**.

## 🎯 About This Project

This repository serves as an interactive learning resource for developers looking to understand and master the latest React features. Each feature is implemented as a standalone demo with clear examples and explanations.

**Why Next.js?** This project uses Next.js to provide full support for all React 19.2 features, including Server Components, `cacheSignal`, and Partial Pre-rendering, which require a React Server Components framework.

## ✨ Features Covered

### React 19.0
- **Actions & `useActionState`** - Modern form handling with automatic pending states
- **`useOptimistic`** - Optimistic UI updates with automatic rollback
- **`use()` Hook** - Read Promises and Context with Suspense integration
- **Ref as Prop** - Direct ref forwarding without `forwardRef`
- **Document Metadata** - Built-in `<title>`, `<meta>`, and `<link>` support
- **Asset Loading APIs** - `preload()`, `prefetchDNS()`, `preconnect()` for performance

### React 19.2
- **`<Activity />`** - Control visibility and prioritization of app sections
- **`useEffectEvent`** - Extract event logic from Effects
- **`cacheSignal`** - Server Component cache lifecycle management ✨ **Fully working with Next.js!**
- **Performance Tracks** - Enhanced Chrome DevTools profiling
- **Partial Pre-rendering** - Hybrid static/dynamic rendering strategy ✨ **Fully working with Next.js!**

## 📋 Prerequisites

- **Node.js** 18.x or higher
- **npm** 9.x or higher (or **yarn**/**pnpm**)
- Modern browser with DevTools (Chrome recommended for Performance Tracks)
- Basic understanding of React fundamentals
- Basic understanding of Next.js (or willingness to learn!)
- Familiarity with TypeScript (optional but recommended)

## 🚀 Getting Started

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd react-19
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Ensure React 19.2 is installed**
   ```bash
   npm install react@19.2 react-dom@19.2
   ```

4. **Configure Next.js**
   Verify `next.config.js` has experimental features enabled:
   ```js
   const nextConfig = {
     experimental: {
       ppr: true, // Partial Pre-rendering
     },
   };
   ```

### Running the Project

```bash
# Development mode
npm run dev

# Build for production
npm run build

# Start production server
npm run start
```

The app will be available at `http://localhost:3000`.

## 📁 Project Structure

```
react-19/
├── app/
│   ├── demos/
│   │   ├── react-19.0/
│   │   │   ├── actions/page.tsx         # useActionState examples
│   │   │   ├── optimistic/page.tsx      # useOptimistic examples
│   │   │   ├── use-hook/page.tsx        # use() hook examples
│   │   │   ├── ref-prop/page.tsx        # Ref as prop examples
│   │   │   ├── metadata/page.tsx        # Document metadata examples
│   │   │   └── asset-loading/page.tsx   # Asset preloading examples
│   │   └── react-19.2/
│   │       ├── activity/page.tsx        # Activity component examples
│   │       ├── use-effect-event/page.tsx # useEffectEvent examples
│   │       ├── cache-signal/page.tsx    # cacheSignal examples (RSC)
│   │       └── partial-prerender/page.tsx # Partial Pre-rendering
│   ├── components/
│   │   └── Navigation.tsx               # Main navigation component
│   ├── layout.tsx                       # Root layout with providers
│   └── page.tsx                         # Home page
├── next.config.js                       # Next.js configuration
├── PLAN.md                              # Detailed implementation guide
├── TASKS.md                             # Implementation checklist
├── README.md                            # This file
└── package.json
```

## 📚 Learning Path

We recommend following this learning path:

0. **Understand Next.js Basics** - Learn Server vs Client Components distinction
1. **Start with the basics** - Read through `PLAN.md` for detailed implementation steps
2. **React 19.0 Features** (Foundation)
   - Begin with Actions (`actions/page.tsx`)
   - Move to Optimistic Updates (`optimistic/page.tsx`)
   - Learn the `use()` hook (`use-hook/page.tsx`) - works great in Server Components!
   - Understand new ref patterns (`ref-prop/page.tsx`)
   - Master metadata management (`metadata/page.tsx`) - Next.js makes this easy!
   - Optimize with asset loading (`asset-loading/page.tsx`)

3. **React 19.2 Features** (Advanced)
   - Explore Activity patterns (`activity/page.tsx`)
   - Master Effect events (`use-effect-event/page.tsx`)
   - Understand cache signals (`cache-signal/page.tsx`) - Server Components only!
   - Profile with Performance Tracks
   - Implement partial pre-rendering (`partial-prerender/page.tsx`) - Next.js exclusive!

4. **Build Real Projects** - Apply multiple features together

## 🎓 Key Learning Objectives

By working through this project, you will:

- ✅ Understand modern React patterns and best practices
- ✅ Learn to build forms without manual loading state management
- ✅ Master optimistic UI updates and error handling
- ✅ Implement efficient data fetching with Suspense
- ✅ Optimize performance with preloading strategies
- ✅ Use React DevTools for performance profiling
- ✅ Apply advanced rendering strategies (partial pre-rendering)

## 🔍 Feature Highlights

### Actions Transform Form Handling
```tsx
const [state, action, isPending] = useActionState(submitForm, initialState);
// No more manual loading states! ✨
```

### Instant UI with Optimistic Updates
```tsx
const [optimisticTodos, addOptimisticTodo] = useOptimistic(todos);
// Users see changes immediately! ⚡
```

### Simplified Async with use()
```tsx
const data = use(fetchPromise);
// No useEffect needed for data fetching! 🎉
```

### No More forwardRef
```tsx
function Input({ ref }) {  // Just works! 🚀
  return <input ref={ref} />;
}
```

## 🛠 Development Tips

- **Fast Refresh** - Changes reflect instantly during development
- **TypeScript** - Full type safety for all React 19 APIs
- **Server Components** - Default to Server Components, use `'use client'` only when needed
- **App Router** - Next.js 13+ App Router with file-system based routing
- **DevTools** - Install React DevTools extension for debugging
- **Performance** - Use Chrome DevTools Performance tab to see React 19.2 tracks
- **Turbopack** - Use `npm run dev --turbo` for faster builds (optional)

## 📖 Resources

- [React 19 Official Release](https://react.dev/blog/2024/12/05/react-19)
- [React 19.2 Official Release](https://react.dev/blog/2025/10/01/react-19-2)
- [React Documentation](https://react.dev)
- [Next.js 15 Documentation](https://nextjs.org/docs)
- [Next.js App Router](https://nextjs.org/docs/app)
- [useActionState API](https://react.dev/reference/react/useActionState)
- [useOptimistic API](https://react.dev/reference/react/useOptimistic)
- [use Hook API](https://react.dev/reference/react/use)
- [Activity Component API](https://react.dev/reference/react/Activity)
- [React Performance Tracks](https://react.dev/reference/dev-tools/react-performance-tracks)
- [Server Components](https://react.dev/reference/rsc/server-components)

## 🤝 Contributing

This is a learning project, but contributions are welcome! Feel free to:

- Report bugs or issues
- Suggest improvements to demos
- Add new examples
- Improve documentation
- Share your learning experience

## 📝 Notes

- **Next.js 15+** is required for full React 19.2 support
- **Server Components** enable `cacheSignal` and Partial Pre-rendering features
- Use `'use client'` directive for interactive components with hooks like `useState`, `useEffect`
- Performance Tracks require React 19.2+ and Chrome browser
- Always check the [official React docs](https://react.dev) for the latest updates

## 🎯 Next Steps

1. Read through `PLAN.md` for detailed implementation steps
2. Set up your development environment
3. Start with the first demo (Actions)
4. Work through each feature systematically
5. Build your own projects using these patterns

## 📄 License

MIT License - Feel free to use this project for learning and reference.

---

**Happy Learning!** 🚀 Master React 19 and build amazing modern web applications.

*Last Updated: February 2026*
