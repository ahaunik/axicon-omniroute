# Design Spec: Dashboard Integration & Multipage Architecture

## 1. Project Goal
Combine the existing Axicon multipage website with the static Office AI Command Center dashboard, creating a unified application where the website remains the primary focus and the dashboard serves as a secure, secondary, authenticated section.

## 2. Architecture
- **Framework:** Next.js (base: `ahaunik/axicon`).
- **Structure:**
  - Public pages (Home, About, Services, Projects, Contact) in the root.
  - New `/login` page for authentication.
  - Protected `/dashboard` routes (Dashboard, CRM, Jobs, etc.).
- **Authentication:** Simple, client-side, local state-based authentication ("admin/admin").

## 3. Navigation & Auth
- **Header:** Update `axicon` header to include a "Dashboard" link.
- **Login:** `/login` page with basic credentials verification.
- **Routing:** Use Next.js layout components to wrap dashboard pages (`/dashboard/*`) with a persistent sidebar, while keeping the main website navigation on top-level pages.

## 4. Component & Logic Migration
- **Components:** Convert static HTML dashboard sections into React components.
- **Logic:** Move `AI for me/script.js` functions into React hooks or utility modules (e.g., `useDashboardState`, `useMatchingAssistant`).
- **State Management:** Use React `useState`/`useContext` or simple local storage wrappers to maintain the simulated dashboard state currently in `script.js`.

## 5. Visual Integration
- **Styling:** Port CSS from `AI for me/style.css` to CSS modules or global styles in Next.js.
- **Consistency:** Ensure dashboard styling (colors, fonts, shadows) integrates seamlessly with the Axicon design system.

## 6. Testing
- Basic validation of login/logout flow.
- Navigation verification between dashboard modules.
- Verification of matching assistant functionality in the new React context.
