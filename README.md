# TrackBot — Shopify Theme

## GitHub-dan Shopify-a Qoşulma Təlimatı

### Addım 1: GitHub Repo Yaradın
1. GitHub.com-a gedin → "New repository" 
2. Ad: `trackbot-store`
3. Public seçin → "Create repository"
4. Bu faylları hamısını repo-ya yükləyin

### Addım 2: Shopify Partner Token Alın
1. Shopify Admin → Settings → Apps and sales channels
2. "Develop apps" → "Create an app"
3. App adı: `GitHub Deploy`
4. "Configure Admin API scopes" bölməsində bunları seçin:
   - `write_themes`
   - `read_themes`
5. "Install app" → "Admin API access token" kopyalayın → bir yerdə saxlayın

### Addım 3: Mağaza URL-ini tapın
Shopify Admin URL-inizdən: `your-store.myshopify.com`

### Addım 4: Theme ID tapın
1. Shopify Admin → Online Store → Themes
2. Aktiv temanızın yanında "..." → "Edit code"
3. URL-dən ID-ni götürün: `.../themes/123456789/...` → `123456789`

### Addım 5: GitHub Secrets Əlavə Edin
GitHub repo-nuzda:
Settings → Secrets and variables → Actions → "New repository secret"

3 secret əlavə edin:
| Secret adı | Dəyər |
|---|---|
| `SHOPIFY_STORE_URL` | `your-store.myshopify.com` |
| `SHOPIFY_ACCESS_TOKEN` | Addım 2-dəki token |
| `SHOPIFY_THEME_ID` | Addım 4-dəki ID |

### Addım 6: Deploy Edin
GitHub-da hər `main` branch-ə push etdikdə avtomatik Shopify-a deploy olacaq!

Manuel deploy üçün:
Actions → "Deploy to Shopify" → "Run workflow"

---

## Fayl Strukturu
```
trackbot-store/
├── .github/
│   └── workflows/
│       └── deploy.yml     ← GitHub Actions
├── assets/
│   ├── base.css           ← Bütün stillər
│   └── main.js            ← JavaScript
├── config/
│   ├── settings_schema.json
│   └── settings_data.json
├── layout/
│   └── theme.liquid       ← Ana layout
├── locales/
│   └── en.default.json
├── sections/
│   ├── header.liquid      ← Naviqasiya
│   └── footer.liquid      ← Footer
└── templates/
    └── index.liquid       ← Ana səhifə
```

## Şəkilləri Dəyişin
`templates/index.liquid` faylında `placehold.co` linkləri var.
Onları öz məhsul şəkillərinizlə əvəz edin:
```liquid
{{ 'product-main.jpg' | asset_url | img_tag }}
```
