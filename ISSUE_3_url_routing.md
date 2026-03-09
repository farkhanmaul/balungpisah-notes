# [Question] URL routing: balungpisah.id vs saksi.balungpisah.id

## ❓ Question / Clarification

### Current Behavior
When I click the **logo** in the header on https://saksi.balungpisah.id/, it navigates to:
- https://saksi.balungpisah.id/ (same subdomain)

### Expected Behavior
Which is the **primary/official** domain?
- https://balungpisah.id/ (main domain)
- https://saksi.balungpisah.id/ (subdomain - current)

### 🤔 Questions

#### 1. Domain Strategy
What is the intended URL structure?
- **Option A:** `balungpisah.id` is main landing, `saksi.balungpisah.id` is the app
- **Option B:** `saksi.balungpisah.id` is the primary URL for everything
- **Option C:** Both should work, but redirect to canonical URL

#### 2. SEO & Canonical URLs
If both exist:
- Which one should be the **canonical URL**?
- Should there be redirects between them?
- How does this affect SEO?

#### 3. Logo Navigation
In `src/components/layout/nav-config.ts` (line 48):
```typescript
{
  label: 'Beranda',
  href: '/',  // This goes to current domain
  icon: Home,
  guestOnly: true,
  showInBottomNav: true,
  showInTopNav: true,
}
```

**Should logo click go to:**
- `/` (current subdomain)
- `https://balungpisah.id` (main landing)
- `https://saksi.balungpisah.id` (explicit)

### 📊 From Documentation
From `balungpisah-landing` README:
- Landing page: **balungpisah-landing** repo
- Purpose: "public landing page & initial issue intake"
- Citizen app: **balungpisah-citizen-app** (this repo)

**Suggestion:**
- `balungpisah.id` → Landing page (informational)
- `saksi.balungpisah.id` → Citizen app (functional)

### 💡 Proposed Solution

If the strategy is:
```
balungpisah.id         → Landing page (marketing, info)
saksi.balungpisah.id   → Citizen app (reports, tracking)
```

Then update `nav-config.ts`:
```typescript
{
  label: 'Beranda',
  href: 'https://balungpisah.id',  // Explicit external link
  icon: Home,
  showInTopNav: true,
}
// OR keep '/' for app home, but update logo separately
```

### 🌐 Current URLs
- Landing: https://balungpisah.id (or is this the same as app?)
- App: https://saksi.balungpisah.id/

### 📝 Additional Context
This came from a user trying to understand:
1. What is the "main" URL to bookmark?
2. Why does the logo keep them on the same subdomain?
3. Should the app and landing be on different subdomains?

---

**Asked by:** farkhanmaul (community user)
**Type:** Question / Design clarification
**Priority:** Low (informational)
