# [UX] Add user email/profile info to user menu dropdown

## 🔍 Problem
As a logged-in user, I can't see which email address I'm currently logged in with. When I click the avatar icon in the top-right corner, the dropdown only shows "Keluar" (Sign Out) button.

This makes it confusing when:
- I have multiple email accounts
- I forgot which email I used to login
- I need to verify my account details

## 🎯 Expected Behavior
When clicking the user avatar, the dropdown should show:
- **User email** (primary identifier)
- **User name** (if available)
- **Sign out** button (already exists)

## 📍 Current Behavior
From the codebase, I can see in `src/components/layout/UserMenu.tsx` (line 24-26):
```typescript
/**
 * Minimal version - only sign out action for now.
 * Will expand when Profil/Tiket features are released.
 */
```

The dropdown only shows:
- Keluar (Sign Out) button

## 💡 Suggested Solution
Update `UserMenu.tsx` to display user information:

```typescript
<DropdownMenuContent align="end" className="w-48">
  <DropdownMenuLabel className="font-normal">
    <div className="flex flex-col space-y-1">
      <p className="text-sm font-medium leading-none">{name || 'Pengguna'}</p>
      <p className="text-muted-foreground text-xs leading-none">{email}</p>
    </div>
  </DropdownMenuLabel>
  <DropdownMenuSeparator />
  <DropdownMenuItem onClick={onSignOut} variant="destructive">
    <LogOut className="size-4" />
    Keluar
  </DropdownMenuItem>
</DropdownMenuContent>
```

**Props need to be updated:**
```typescript
interface UserMenuProps {
  name?: string;
  email?: string;  // Add this
  avatarUrl?: string;
  onSignOut: () => void;
}
```

## 🌐 Environment
- URL: https://saksi.balungpisah.id/
- Page: All authenticated pages
- Role: Logged-in user

## 📝 Additional Context
This is a common UX pattern in modern web apps. Users need to know which account they're currently using, especially when they have multiple accounts or share devices.

---

**Reported by:** farkhanmaul (community user)
**Severity:** Low (UX improvement)
**Priority:** Medium
