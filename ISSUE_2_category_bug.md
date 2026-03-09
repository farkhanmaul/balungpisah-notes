# [Bug] Category field shows empty border on /my-reports page

## 🐛 Bug Description
On the "Laporan Saya" (My Reports) page at https://saksi.balungpisah.id/my-reports/, the category field for each report only shows:
- A colored dot (circle)
- Empty border
- No category name/text

## 📍 Steps to Reproduce
1. Login to https://saksi.balungpisah.id/
2. Navigate to "Laporan Saya" or go directly to https://saksi.balungpisah.id/my-reports/
3. Look at any report card
4. Observe the category field (next to the location)

## 🎯 Expected Behavior
The category field should display:
- Colored dot (✅ this works)
- **Category name** (❌ missing - e.g., "Infrastruktur", "Kebersihan", etc.)

## 📍 Current Behavior
Only shows:
- Colored dot
- Empty space where category name should be

## 🔍 Code Analysis
From `src/app/my-reports/page.tsx` (lines 187-197):
```typescript
{report.categories?.[0] && (
  <span className="inline-flex items-center gap-1">
    <span
      className="h-2 w-2 rounded-full"
      style={{
        backgroundColor: report.categories[0].color || '#94a3b8',
      }}
    />
    {report.categories[0].category_name ?? 'Umum'}
  </span>
)}
```

From `src/features/my-reports/types/index.ts` (line 14-20):
```typescript
export interface IReportCategoryDto {
  category_id: string;
  category_name?: string | null;
  category_slug?: string | null;
  severity: 'low' | 'medium' | 'high' | 'critical';
  color?: string | null;
}
```

## 💡 Possible Root Causes

### 1. Backend API Issue (Most Likely)
The backend API (`GET /api/reports`) is not returning `category_name` in the response.

**Check:**
- Backend endpoint: `balungpisah-core` API
- Database query might not be joining the categories table
- Response might only include `category_id` without the name

### 2. Data Migration Issue
Categories exist in database but:
- Names are NULL
- Or category names not properly seeded

### 3. API Response Structure
The API response might have different structure than expected:
```typescript
// Current expectation
report.categories[0].category_name

// Actual might be:
report.category_name
// or
report.categories[0].name
```

## 🛠️ Suggested Debugging Steps

### 1. Check API Response
Add temporary console.log in `my-reports/page.tsx`:
```typescript
console.log('Report data:', report);
console.log('Categories:', report.categories);
```

### 2. Verify Backend Query
Check `balungpisah-core` for the `/api/reports` endpoint and verify:
- Categories are being joined properly
- All category fields are being selected

### 3. Fallback UI
While fixing backend, improve the fallback:
```typescript
{report.categories[0]?.category_name || report.category_name || 'Kategori: ' + report.categories[0]?.category_id}
```

## 🌐 Environment
- URL: https://saksi.balungpisah.id/my-reports/
- Browser: Any
- Role: Authenticated user with reports

## 📝 Additional Context
This affects all users trying to identify their report categories. The category is important for filtering and understanding the report type at a glance.

---

**Reported by:** farkhanmaul (community user)
**Severity:** Medium (data display issue)
**Priority:** Medium
