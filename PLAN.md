# React 19 & 19.2 Features Showcase - Learning Plan

A comprehensive guide to learn and implement all major features introduced in React 19.0 and React 19.2 using **Next.js 15+**.

## Project Architecture: One App, Multiple Demos

This project is structured as **one unified Next.js application** with multiple pages/routes, not separate standalone projects:

- **One codebase** - Single Next.js project with shared dependencies
- **Multiple routes** - Each feature gets its own page under `/demos/`
- **Shared components** - Navigation and layout components used across all demos
- **Easy navigation** - Switch between features without changing projects
- **Integration examples** - Later sections combine multiple features in single pages

### Benefits of This Approach

1. **Realistic Architecture** - Real apps use multiple features together
2. **Reduced Overhead** - One set of dependencies, one build process
3. **Easy Comparison** - Navigate between demos without switching projects
4. **Shared Learning** - See patterns and utilities reused across features
5. **Integration Ready** - Combine multiple features in later demos

## Why Next.js?

Next.js provides **full support for all React 19.2 features** in one project:
- ✅ **Server Components** - Enable `cacheSignal` and advanced patterns
- ✅ **Partial Pre-rendering** - Built-in support via experimental flag
- ✅ **App Router** - File-based routing (no react-router needed!)
- ✅ **Metadata API** - Simplified SEO management per route
- ✅ **Production Ready** - Easy deployment to Vercel

## Prerequisites

- Node.js 18+ installed
- Familiarity with React basics
- Understanding of async/await and Promises
- Basic knowledge of TypeScript (optional but recommended)
- Understanding of Next.js App Router (recommended)

## Server Components vs Client Components

**Next.js 13+ defaults to Server Components.** Understanding when to use each is crucial:

### Server Components (Default)
- No `'use client'` directive needed
- Great for: data fetching, SEO, static content
- Can use: `async/await`, `cache()`, `cacheSignal`
- Cannot use: `useState`, `useEffect`, event handlers

### Client Components
- Require `'use client'` directive at the top
- Great for: interactivity, browser APIs, state management
- Can use: all hooks, event handlers, browser APIs
- Run on both server (SSR) and client (hydration)

**Rule of Thumb:** Start with Server Components, add `'use client'` only when you need interactivity!

## Project Setup

1. **Initialize Next.js Project**
   ```bash
   npx create-next-app@latest react-19-showcase
   ```
   
   When prompted, select:
   - ✅ TypeScript: Yes
   - ✅ ESLint: Yes
   - ✅ Tailwind CSS: Yes
   - ✅ `src/` directory: No (use `app/` dir)
   - ✅ App Router: Yes
   - ✅ Turbopack: Your choice
   - ✅ Import alias: Default (@/*)

   ```bash
   cd react-19-showcase
   ```

2. **Ensure React 19.2 is installed**
   ```bash
   npm install react@19.2 react-dom@19.2
   ```

3. **Configure Next.js for React 19**
   Update `next.config.js`:
   ```js
   /** @type {import('next').NextConfig} */
   const nextConfig = {
     experimental: {
       ppr: true, // Enable Partial Pre-rendering
     },
   };
   export default nextConfig;
   ```

4. **Project Structure** (One app, multiple pages)
   ```
   app/                                  # Single Next.js App Router
   ├── demos/                            # All demos in one place
   │   ├── react-19.0/                   # React 19.0 feature demos
   │   │   ├── actions/page.tsx          # /demos/react-19.0/actions
   │   │   ├── optimistic/page.tsx       # /demos/react-19.0/optimistic
   │   │   ├── use-hook/page.tsx         # /demos/react-19.0/use-hook
   │   │   ├── ref-prop/page.tsx         # /demos/react-19.0/ref-prop
   │   │   ├── metadata/page.tsx         # /demos/react-19.0/metadata
   │   │   └── asset-loading/page.tsx    # /demos/react-19.0/asset-loading
   │   └── react-19.2/                   # React 19.2 feature demos
   │       ├── activity/page.tsx         # /demos/react-19.2/activity
   │       ├── use-effect-event/page.tsx # /demos/react-19.2/use-effect-event
   │       ├── cache-signal/page.tsx     # /demos/react-19.2/cache-signal
   │       └── partial-prerender/page.tsx # /demos/react-19.2/partial-prerender
   ├── components/
   │   └── Navigation.tsx                # Shared navigation (all pages)
   ├── layout.tsx                        # Root layout (wraps all pages)
   └── page.tsx                          # Home page (/) with demo list
   ```

   **Key Point:** This is ONE project. You'll run `npm run dev` once and navigate between `/demos/react-19.0/actions`, `/demos/react-19.0/optimistic`, etc.

---

## React 19.0 Features

### 1. Actions & Form Handling with `useActionState`

**What it is:** A new hook that manages form actions with automatic pending states and error handling.

**Key Concepts:**
- Replaces `useFormState` (deprecated name)
- Automatically handles pending states
- Built-in error state management
- Works with server and client actions

**Implementation Steps:**

1. **Create a Basic Form (app/demos/react-19.0/actions/page.tsx)**
   - Mark component with `'use client'` directive
   - Import `useActionState` from 'react'
   - Create an async action function that simulates form submission
   - Use `useActionState(actionFn, initialState)`
   - Display pending state while action is running
   - Show success/error messages

2. **Add Form Validation**
   - Add client-side validation in the action function
   - Return error messages in the state
   - Display field-specific errors

3. **Progressive Enhancement**
   - Make the form work without JavaScript
   - Use `formAction` attribute for form submission
   - Test with JS disabled in browser

**Learning Goals:**
- Understand how Actions eliminate manual loading state
- Learn the difference between Actions and regular event handlers
- Master form handling without useState

---

### 2. Optimistic Updates with `useOptimistic`

**What it is:** A hook that allows you to show optimistic UI updates before the server confirms changes.

**Key Concepts:**
- Instant UI feedback
- Automatic rollback on error
- Works with Actions
- Improves perceived performance

**Implementation Steps:**

1. **Create a Todo List (app/demos/react-19.0/optimistic/page.tsx)**
   - Mark component with `'use client'` directive
   - Set up a list of todos with local state
   - Create an async function to add todos (simulate API delay)
   - Use `useOptimistic` to show immediate updates
   - Show the optimistic item with a visual indicator

2. **Handle Deletions Optimistically**
   - Add delete functionality with optimistic update
   - Show strikethrough or fade-out animation
   - Restore item on error

3. **Error Handling**
   - Simulate server errors (random failure)
   - Show error message when optimistic update fails
   - Watch the automatic rollback behavior

**Learning Goals:**
- Understand optimistic UI patterns
- Learn when to use optimistic updates
- Master error recovery in optimistic scenarios

---

### 3. Resource Loading with `use()`

**What it is:** A new hook that lets you read the value of a Promise or Context.

**Key Concepts:**
- Can be called conditionally (unlike other hooks)
- Works with Suspense boundaries
- Simplifies async data fetching
- No need for useEffect for data loading

**Implementation Steps:**

1. **Create a Data Fetching Demo (app/demos/react-19.0/use-hook/page.tsx)**
   - This can be a Server Component (no 'use client' needed!)
   - Create an async function that fetches data
   - Wrap component with `<Suspense>` boundary
   - Use `use(promise)` to read the data
   - Add loading fallback

2. **Compare with useEffect Approach**
   - Create side-by-side comparison
   - Show traditional useEffect + useState pattern
   - Highlight code simplification

3. **Conditional Usage**
   - Demonstrate calling `use()` inside conditions
   - Show how it differs from other hooks

**Learning Goals:**
- Understand the power of `use()` with Suspense
- Learn when to use `use()` vs `useEffect`
- Master Promise handling in components

---

### 4. Ref as Prop (No More forwardRef)

**What it is:** Components can now accept `ref` as a regular prop, eliminating the need for `forwardRef`.

**Key Concepts:**
- `ref` is now a standard prop
- Simpler component APIs
- TypeScript support is cleaner
- `forwardRef` is deprecated but still works

**Implementation Steps:**

1. **Create a Custom Input Component (app/demos/react-19.0/ref-prop/page.tsx)**
   - Mark component with `'use client'` directive
   - Create a component that accepts `ref` as a prop
   - Forward the ref to a DOM element
   - Add custom functionality (e.g., focus method)

2. **Create a Parent Component**
   - Use `useRef` to create a ref
   - Pass it to your custom component
   - Add buttons to interact with the ref (focus, clear)

3. **Compare Old vs New Pattern**
   - Show commented-out forwardRef version
   - Highlight the simplified code

**Learning Goals:**
- Understand the ref forwarding pattern
- Learn how to expose imperative handles
- Master ref usage in custom components

---

### 5. Document Metadata (Title, Meta, Link)

**What it is:** You can now render `<title>`, `<meta>`, and `<link>` tags directly in components, and React automatically hoists them to `<head>`.

**Key Concepts:**
- Metadata lives with component code
- Automatic deduplication
- Works with SSR
- Better than helmet/third-party solutions

**Implementation Steps:**

1. **Create Multiple Pages (app/demos/react-19.0/metadata/)**
   - Use Next.js Metadata API in page.tsx files
   - Export metadata object from each page
   - Add dynamic metadata with generateMetadata function
   - Add unique titles and descriptions per route

2. **Add Open Graph Tags**
   - Add OG tags for social sharing
   - Include og:title, og:description, og:image
   - Test in social media debuggers

3. **Add Favicons and Theme Colors**
   - Add `<link>` tags for favicons
   - Add theme-color meta tag
   - Test switching between pages

**Learning Goals:**
- Understand metadata hoisting
- Learn SEO best practices with React
- Master document head management

---

### 6. Asset Loading APIs

**What it is:** New functions to preload resources and optimize loading performance.

**Key Concepts:**
- `preload()` - Preload critical resources
- `prefetchDNS()` - Early DNS resolution
- `preconnect()` - Establish early connections
- Stylesheet precedence control

**Implementation Steps:**

1. **Create Resource Preloading Demo (app/demos/react-19.0/asset-loading/page.tsx)**
   - Mark component with `'use client'` directive
   - Import preloading functions from 'react-dom'
   - Preload fonts before they're needed
   - Preload images for next page

2. **DNS Prefetching**
   - Add `prefetchDNS()` for external domains
   - Demonstrate early DNS resolution

3. **Connection Prewarming**
   - Use `preconnect()` for API domains
   - Show performance improvements in Network tab

**Learning Goals:**
- Understand resource loading priorities
- Learn performance optimization techniques
- Master browser resource hints

---

## React 19.2 Features

### 7. Activity Component

**What it is:** A component that lets you control and prioritize parts of your app with `visible` and `hidden` modes.

**Key Concepts:**
- Alternative to conditional rendering
- `hidden` mode: unmounts effects, defers updates
- `visible` mode: normal rendering
- Pre-render content without performance impact

**Implementation Steps:**

1. **Create Tab Navigation (app/demos/react-19.2/activity/page.tsx)**
   - Mark component with `'use client'` directive
   - Create 3 tabs with heavy content
   - Use `<Activity mode={isVisible ? 'visible' : 'hidden'}>` for each tab
   - Compare with traditional conditional rendering

2. **Pre-render Hidden Tabs**
   - Render all tabs but keep inactive ones hidden
   - Measure time to switch tabs
   - Compare with lazy loading approach

3. **State Preservation**
   - Add form inputs in tabs
   - Switch between tabs
   - Verify state is preserved when returning

**Learning Goals:**
- Understand when to use Activity vs conditional rendering
- Learn performance implications of pre-rendering
- Master navigation state management

---

### 8. useEffectEvent Hook

**What it is:** Extract event-like logic from Effects without adding it to the dependency array.

**Key Concepts:**
- Solves the "reactive vs event" problem
- Functions wrapped in useEffectEvent always see latest props
- Not added to dependency arrays
- Prevents unnecessary Effect re-runs

**Implementation Steps:**

1. **Create Chat Room Example (app/demos/react-19.2/use-effect-event/page.tsx)**
   - Mark component with `'use client'` directive
   - Build a component with roomId and theme props
   - Create a connection Effect that shows notifications
   - Show the problem: theme changes cause reconnection

2. **Apply useEffectEvent**
   - Extract notification logic to useEffectEvent
   - Keep only roomId in dependencies
   - Verify theme changes don't cause reconnection

3. **Add Analytics Example**
   - Create Effect that logs page views
   - Extract event tracking to useEffectEvent
   - Show how it accesses latest props without causing re-runs

**Learning Goals:**
- Understand the "reactive" vs "event" distinction
- Learn when to use useEffectEvent
- Master Effect dependency management

---

### 9. cacheSignal (Server Components)

**What it is:** Know when the `cache()` lifetime is over in Server Components.

**Key Concepts:**
- Only for React Server Components
- Used with `cache()` API
- Allows cleanup when cache expires
- Enables request abortion

**Implementation Steps:**

1. **Set Up Server Component (app/demos/react-19.2/cache-signal/page.tsx)**
   - This is a Server Component (no 'use client' directive!)
   - Import `cache` and `cacheSignal` from 'react'
   - Create cached fetch function with deduplication

2. **Use cacheSignal for Cleanup**
   - Pass cacheSignal to fetch as AbortSignal
   - Log when signal is aborted
   - Understand the cache lifecycle

3. **Handle Abort Events**
   - Add event listener to cacheSignal
   - Clean up resources on abort
   - Test with rapid navigation

**Learning Goals:**
- Understand Server Component caching
- Learn resource cleanup patterns
- Master AbortController integration

---

### 10. Performance Tracks (Chrome DevTools)

**What it is:** New custom tracks in Chrome DevTools to visualize React's internal work.

**Key Concepts:**
- Scheduler track: Shows priority-based work
- Components track: Shows rendering and effects
- Helps identify performance bottlenecks
- Integrated with Chrome DevTools

**Implementation Steps:**

1. **Set Up Performance Monitoring**
   - Open Chrome DevTools
   - Navigate to Performance tab
   - Record a session with your React app

2. **Create Test Scenarios**
   - Build a component with heavy rendering
   - Add startTransition for non-urgent updates
   - Create state updates with different priorities

3. **Analyze Tracks**
   - Identify "Scheduler ⚛" track
   - Identify "Components ⚛" track
   - Look for blocked renders
   - Find long-running effects

**Learning Goals:**
- Understand React's scheduling system
- Learn to identify performance issues
- Master DevTools profiling

---

### 11. Partial Pre-rendering

**What it is:** Pre-render static parts of your app and resume rendering dynamic content later.

**Key Concepts:**
- Split rendering into static shell + dynamic content
- Static parts served from CDN
- Resume rendering for personalized content
- Hybrid SSG + SSR approach

**Implementation Steps:**

1. **Set Up Pre-rendering (app/demos/react-19.2/partial-prerender/page.tsx)**
   - Enable PPR in next.config.js (experimental.ppr: true)
   - Create static shell wrapper component
   - Use Suspense boundaries to separate static/dynamic content
   - Static parts render immediately, dynamic parts stream in

2. **Implement Resume**
   - Load postponed state from server
   - Use `resume()` to continue rendering
   - Stream dynamic content to client

3. **Test the Flow**
   - Generate pre-rendered HTML
   - Serve from CDN
   - Resume with user-specific data

**Learning Goals:**
- Understand static vs dynamic content separation
- Learn advanced SSR techniques
- Master partial hydration concepts

---

## Additional Exercises

### Integration Challenges (All in One Project!)

Build additional pages that combine multiple features:

1. **Build a Blog Platform** (`app/examples/blog/page.tsx`)
   - Use Activity for tab navigation
   - Use metadata for SEO
   - Use Actions for comments
   - Use useOptimistic for likes
   - **All features working together in one page!**

2. **Create E-commerce Cart** (`app/examples/cart/page.tsx`)
   - Use Actions for add-to-cart
   - Use useOptimistic for quantity updates
   - Preload product images
   - Use useEffectEvent for analytics
   - **Demonstrate feature composition**

3. **Build Real-time Dashboard** (`app/examples/dashboard/page.tsx`)
   - Use use() for data fetching
   - Use Activity for hidden widgets
   - Use Performance Tracks to optimize
   - Use useEffectEvent for WebSocket
   - **Show advanced patterns**

These integration examples show the real power of having all features in one project!

---

## Testing Your Knowledge

After implementing each feature, ask yourself:

1. What problem does this feature solve?
2. When should I use this vs alternatives?
3. What are the performance implications?
4. How does it work with SSR?
5. What are the edge cases?

---

## Resources

- [React 19 Release Blog](https://react.dev/blog/2024/12/05/react-19)
- [React 19.2 Release Blog](https://react.dev/blog/2025/10/01/react-19-2)
- [React Docs](https://react.dev)
- [Next.js 15 Documentation](https://nextjs.org/docs)
- [Server Components](https://react.dev/reference/rsc/server-components)
- [useActionState Docs](https://react.dev/reference/react/useActionState)
- [useOptimistic Docs](https://react.dev/reference/react/useOptimistic)
- [use Hook Docs](https://react.dev/reference/react/use)
- [Activity Component Docs](https://react.dev/reference/react/Activity)
- [useEffectEvent Docs](https://react.dev/learn/separating-events-from-effects)
- [Next.js Metadata API](https://nextjs.org/docs/app/building-your-application/optimizing/metadata)
- [Partial Pre-rendering](https://nextjs.org/docs/app/building-your-application/rendering/partial-prerendering)

---

## Tips for Learning

1. **Build Incrementally** - Add one page/route at a time to the project
2. **One Feature at a Time** - Don't rush, master each feature before moving on
3. **Read the Docs** - Official docs have great examples and explanations
4. **Break Things** - Intentionally cause errors to understand edge cases
5. **Compare Patterns** - Navigate between pages to compare approaches
6. **Reuse Code** - Extract shared components and utilities as you go
7. **Build Real Projects** - Add integration examples that combine multiple features
8. **Performance Profile** - Use Chrome DevTools across all pages to see differences
9. **Share Your Learning** - Write blog posts or create tutorials based on your project

**Remember:** You're building ONE application. Think about how the Navigation component, shared utilities, and consistent styling can serve all your demo pages!

---

## Next Steps

1. Set up ONE Next.js project with the structure above
2. Create the root layout and navigation (shared across all pages)
3. Build a home page that lists all available demos
4. Start implementing React 19.0 features (pages 1-6), one route at a time
5. Move to React 19.2 features (pages 7-11), building on your existing project
6. Add integration examples that combine multiple features
7. Profile and optimize the entire application
8. Deploy your complete showcase app!

Good luck with your React 19 learning journey! 🚀

**Remember:** You're building one cohesive application, not a collection of separate demos. Think about the user experience of navigating through your feature showcase!
