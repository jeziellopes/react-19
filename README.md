# React 19 & 19.2 Features Showcase

> **📚 Study Project - Work in Progress**  
> This is a personal study project where I'm planning and building a comprehensive learning resource for React 19.0 and 19.2 features. The documentation (PLAN.md and TASKS.md) is complete, but the actual demos are still being implemented.

A comprehensive learning project demonstrating all major features introduced in React 19.0 and React 19.2, built as **one unified Next.js 15+ application** with multiple demo pages.

## 🎯 About This Project

This repository is designed as an interactive learning resource for developers (including myself!) looking to understand and master the latest React features. The goal is to build **one Next.js project** with dedicated pages/routes for each feature, allowing you to navigate between demos and see all features working together.

**Structure:** One Next.js app → Multiple routes → Each route demonstrates a specific React 19+ feature

**Current Status:** 📋 Planning & Documentation Phase → 🚧 Implementation Coming Soon

**Why Next.js?** Next.js provides full support for all React 19.2 features, including Server Components, `cacheSignal`, and Partial Pre-rendering, which require a React Server Components framework. Plus, the App Router makes it easy to organize multiple demos in one project.

### How It Works

1. **One Installation** - `npm install` once, get all dependencies
2. **One Dev Server** - `npm run dev` once, access all demos
3. **One Codebase** - Share components, utilities, and styles across features
4. **Multiple Routes** - Navigate between `/demos/react-19.0/actions`, `/demos/react-19.0/optimistic`, etc.
5. **Easy Comparison** - See how different features integrate within the same app

This approach makes it easier to understand how features work together in a real application, rather than isolated examples.

## ✨ Features Covered (All in One Project!)

### React 19.0
- **Actions & `useActionState`** - `/demos/react-19.0/actions` - Modern form handling
- **`useOptimistic`** - `/demos/react-19.0/optimistic` - Optimistic UI updates
- **`use()` Hook** - `/demos/react-19.0/use-hook` - Promise handling with Suspense
- **Ref as Prop** - `/demos/react-19.0/ref-prop` - Direct ref forwarding
- **Document Metadata** - `/demos/react-19.0/metadata` - Built-in SEO support
- **Asset Loading APIs** - `/demos/react-19.0/asset-loading` - Performance optimization

### React 19.2
- **`<Activity />`** - `/demos/react-19.2/activity` - Control visibility and prioritization
- **`useEffectEvent`** - `/demos/react-19.2/use-effect-event` - Extract event logic
- **`cacheSignal`** - `/demos/react-19.2/cache-signal` - Server cache management ✨
- **Performance Tracks** - Chrome DevTools profiling throughout the app
- **Partial Pre-rendering** - `/demos/react-19.2/partial-prerender` - Hybrid rendering ✨

## 📋 Prerequisites

- **Node.js** 18.x or higher
- **npm** 9.x or higher (or **yarn**/**pnpm**)
- Modern browser with DevTools (Chrome recommended for Performance Tracks)
- Basic understanding of React fundamentals
- Basic understanding of Next.js (or willingness to learn!)
- Familiarity with TypeScript (optional but recommended)

## 🚀 Getting Started

> **Note:** The project implementation is currently in progress. The setup instructions below are for when the project is ready to run. For now, you can explore the planning documents ([PLAN.md](PLAN.md) and [TASKS.md](TASKS.md)) to understand the roadmap.

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd react-19
   ```

2. **Install dependencies** (when implementation begins)
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

### Running the Project (Coming Soon)

```bash
# Development mode - start once, access all demos
npm run dev

# Build for production - builds entire app with all demos
npm run build

# Start production server
npm run start
```

The app will be available at `http://localhost:3000` with:
- Home page: `http://localhost:3000/`
- Actions demo: `http://localhost:3000/demos/react-19.0/actions`
- Optimistic demo: `http://localhost:3000/demos/react-19.0/optimistic`
- And so on... all features in one running application!

## 📁 Project Structure

> **Note:** This is ONE Next.js project with multiple demo pages. Implementation is in progress.

```
react-19/                                # 👈 Single Next.js project
├── app/
│   ├── demos/                           # All demos live here
│   │   ├── react-19.0/                  # React 19.0 features
│   │   │   ├── actions/page.tsx         # Route: /demos/react-19.0/actions
│   │   │   ├── optimistic/page.tsx      # Route: /demos/react-19.0/optimistic
│   │   │   ├── use-hook/page.tsx        # Route: /demos/react-19.0/use-hook
│   │   │   ├── ref-prop/page.tsx        # Route: /demos/react-19.0/ref-prop
│   │   │   ├── metadata/page.tsx        # Route: /demos/react-19.0/metadata
│   │   │   └── asset-loading/page.tsx   # Route: /demos/react-19.0/asset-loading
│   │   └── react-19.2/                  # React 19.2 features
│   │       ├── activity/page.tsx        # Route: /demos/react-19.2/activity
│   │       ├── use-effect-event/page.tsx # Route: /demos/react-19.2/use-effect-event
│   │       ├── cache-signal/page.tsx    # Route: /demos/react-19.2/cache-signal
│   │       └── partial-prerender/page.tsx # Route: /demos/react-19.2/partial-prerender
│   ├── components/
│   │   └── Navigation.tsx               # Shared across all pages
│   ├── layout.tsx                       # Root layout (wraps everything)
│   └── page.tsx                         # Home page with feature list
├── next.config.js                       # Next.js configuration
├── PLAN.md                              # Detailed implementation guide ✅
├── TASKS.md                             # Implementation checklist ✅
├── README.md                            # This file ✅
└── package.json
```

## 📚 Learning Path

**Recommended approach once demos are implemented:**

0. **Understand Next.js Basics** - Learn Server vs Client Components distinction
1. **Start with the basics** - Read through [PLAN.md](PLAN.md) for detailed implementation steps
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

**Current Focus:** Working through the implementation following this exact path! Track progress in [TASKS.md](TASKS.md).

## 🎓 Learning Objectives

Through building this **unified Next.js project**, the goals are to:

- ✅ Understand modern React patterns and best practices
- ✅ Learn to build forms without manual loading state management
- ✅ Master optimistic UI updates and error handling
- ✅ Implement efficient data fetching with Suspense
- ✅ Optimize performance with preloading strategies
- ✅ Use React DevTools for performance profiling
- ✅ Apply advanced rendering strategies (partial pre-rendering)
- ✅ Gain hands-on experience with Server Components
- ✅ Build a comprehensive reference project for React 19+
- ✅ See how multiple features work together in one application

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

This is primarily a personal learning project, but suggestions and feedback are welcome! Feel free to:

- Open issues with suggestions or corrections
- Share ideas for better demo implementations
- Report any errors in the documentation
- Share your own learning experience with React 19

**Note:** As this is a study project, pull requests will be reviewed carefully to ensure they align with the learning objectives.

## 📊 Project Status

- ✅ **Documentation Complete** - PLAN.md and TASKS.md ready
- ✅ **Next.js Setup** - Configuration and structure planned
- 🚧 **Implementation In Progress** - Demos being built one by one
- ⏳ **Deployment** - Coming after implementation

Track progress in [TASKS.md](TASKS.md)!

## 📝 Notes

- **Next.js 15+** is required for full React 19.2 support
- **Server Components** enable `cacheSignal` and Partial Pre-rendering features
- Use `'use client'` directive for interactive components with hooks like `useState`, `useEffect`
- Performance Tracks require React 19.2+ and Chrome browser
- Always check the [official React docs](https://react.dev) for the latest updates

## 🎯 Next Steps

**For following along with this study project:**

1. ⭐ Star this repo to follow the progress
2. 📖 Read through [PLAN.md](PLAN.md) for detailed implementation guide
3. ✅ Check [TASKS.md](TASKS.md) for current progress
4. 🔔 Watch for updates as demos are implemented
5. 💬 Open discussions/issues with questions or suggestions

**For building your own version:**

1. Read through `PLAN.md` for detailed implementation steps
2. Set up your development environment
3. Start with the first demo (Actions)
4. Work through each feature systematically
5. Build your own projects using these patterns

## 📄 License

MIT License - Feel free to use this project for learning and reference.

---

**Let's Learn Together!** 🚀 Follow along as I build this comprehensive study project for React 19 and master modern web development.

*Project Status: 📋 Planning Complete → 🚧 Implementation In Progress*  
*Last Updated: February 11, 2026*
