# React 19 & 19.2 Features Showcase

A comprehensive learning project demonstrating all major features introduced in React 19.0 and React 19.2, with hands-on examples and implementation guides.

## 🎯 About This Project

This repository serves as an interactive learning resource for developers looking to understand and master the latest React features. Each feature is implemented as a standalone demo with clear examples and explanations.

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
- **`cacheSignal`** - Server Component cache lifecycle management
- **Performance Tracks** - Enhanced Chrome DevTools profiling
- **Partial Pre-rendering** - Hybrid static/dynamic rendering strategy

## 📋 Prerequisites

- **Node.js** 18.x or higher
- **npm** 9.x or higher (or **yarn**/**pnpm**)
- Modern browser with DevTools (Chrome recommended for Performance Tracks)
- Basic understanding of React fundamentals
- Familiarity with TypeScript (optional)

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

### Running the Project

```bash
# Development mode
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

The app will be available at `http://localhost:5173` (or another port if 5173 is in use).

## 📁 Project Structure

```
react-19/
├── src/
│   ├── demos/
│   │   ├── react-19.0/
│   │   │   ├── ActionsDemo.tsx          # useActionState examples
│   │   │   ├── OptimisticDemo.tsx      # useOptimistic examples
│   │   │   ├── UseDemo.tsx             # use() hook examples
│   │   │   ├── RefDemo.tsx             # Ref as prop examples
│   │   │   ├── MetadataDemo.tsx        # Document metadata examples
│   │   │   └── AssetLoadingDemo.tsx    # Asset preloading examples
│   │   └── react-19.2/
│   │       ├── ActivityDemo.tsx         # Activity component examples
│   │       ├── UseEffectEventDemo.tsx  # useEffectEvent examples
│   │       ├── CacheSignalDemo.tsx     # cacheSignal examples
│   │       └── PartialPrerenderingDemo.tsx
│   ├── components/
│   │   └── Navigation.tsx              # Main navigation component
│   ├── App.tsx                         # Root application component
│   └── main.tsx                        # Application entry point
├── PLAN.md                             # Detailed implementation guide
├── README.md                           # This file
└── package.json
```

## 📚 Learning Path

We recommend following this learning path:

1. **Start with the basics** - Read through `PLAN.md` for detailed implementation steps
2. **React 19.0 Features** (Foundation)
   - Begin with Actions (`ActionsDemo.tsx`)
   - Move to Optimistic Updates (`OptimisticDemo.tsx`)
   - Learn the `use()` hook (`UseDemo.tsx`)
   - Understand new ref patterns (`RefDemo.tsx`)
   - Master metadata management (`MetadataDemo.tsx`)
   - Optimize with asset loading (`AssetLoadingDemo.tsx`)

3. **React 19.2 Features** (Advanced)
   - Explore Activity patterns (`ActivityDemo.tsx`)
   - Master Effect events (`UseEffectEventDemo.tsx`)
   - Understand cache signals (`CacheSignalDemo.tsx`)
   - Profile with Performance Tracks
   - Implement partial pre-rendering

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

- **Hot Module Replacement** - Changes reflect instantly during development
- **TypeScript** - Full type safety for all React 19 APIs
- **DevTools** - Install React DevTools extension for debugging
- **Performance** - Use Chrome DevTools Performance tab to see React 19.2 tracks

## 📖 Resources

- [React 19 Official Release](https://react.dev/blog/2024/12/05/react-19)
- [React 19.2 Official Release](https://react.dev/blog/2025/10/01/react-19-2)
- [React Documentation](https://react.dev)
- [useActionState API](https://react.dev/reference/react/useActionState)
- [useOptimistic API](https://react.dev/reference/react/useOptimistic)
- [use Hook API](https://react.dev/reference/react/use)
- [Activity Component API](https://react.dev/reference/react/Activity)
- [React Performance Tracks](https://react.dev/reference/dev-tools/react-performance-tracks)

## 🤝 Contributing

This is a learning project, but contributions are welcome! Feel free to:

- Report bugs or issues
- Suggest improvements to demos
- Add new examples
- Improve documentation
- Share your learning experience

## 📝 Notes

- Some features (like `cacheSignal` and Partial Pre-rendering) require Server Component support (Next.js, Remix, etc.)
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
