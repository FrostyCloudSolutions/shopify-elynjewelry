# ElynJewelry.com — Shopify Store Recovery & Development

**Developer:** Frosty Solutions  
**Website:** frostycloud.net  
**Platform:** Shopify Basic  
**Theme:** Dawn v15.4.1  
**Domain:** elynjewelry.com (Alibaba Cloud managed)  
**Project Duration:** ~5 days full time  
**Status:** MVP Delivered — March 2026  

---

## Project Summary

ElynJewelry is a Chinese-owned international pearl jewelry e-commerce store 
targeting global customers. The client had previously engaged a developer who 
left the store in a non-functional state with numerous bugs, inconsistencies, 
and a Chinese-only configuration incompatible with international sales.

Frosty Solutions was engaged to recover, rebuild, and optimize the store to a 
functional MVP standard. This project involved theme migration, store 
configuration recovery, inventory reorganization, multilanguage 
internationalization, and client handoff documentation.

---

## Tech Stack

| Component | Details |
|---|---|
| Platform | Shopify Basic |
| Theme | Dawn v15.4.1 |
| Domain Registrar | Alibaba Cloud |
| DNS | Alibaba Cloud → Shopify |
| Payment Gateway | PayPal |
| Apps | Geolocation - GLC, Search & Discovery |
| Languages | 11 (English default) |
| Currency | USD |
| Languages Used | Liquid, JSON |

---

## Problems Inherited from Previous Developer

### 1. Broken Horizon Theme
The store was running a heavily customized Horizon theme with multiple layout 
bugs, broken collection displays, and non-functional theme editor sections.

**Root Cause:** Horizon theme collection section architecture uses single-block 
template rendering, making independent 4-collection configuration impossible 
without code modification.

**Resolution:** Migrated to Dawn v15.4.1.

---

### 2. Chinese-Only Store Configuration
The entire store was configured as a China-only installation:
- Business entity: 我的商店 (China)
- Timezone: GMT+8 Beijing
- Only active market: 中国 (China)
- Store defaulting to Chinese for all visitors globally

**Investigation Path (all ruled out before finding root cause):**
- Language settings in Shopify admin
- Locale JSON files (zh-CN.json, zh-TW.json)
- Translate & Adapt app
- Markets settings
- Theme default content editor
- Store general settings

**Root Cause:** Previous developer created a navigation menu named 主菜单 
(Chinese for "Main Menu") which was the active menu referenced by all theme 
templates. Menu items named in Chinese (主页, 产品目录, 联系方式) rendered 
as site navigation for all visitors regardless of language settings.

**Resolution:** Created new English Main Menu in Content → Menus. Redirected 
Dawn theme header to reference new English menu via Theme Editor → Header → 
Menu setting.

**Key Lesson:** Always check which menu the theme header is pointing at before 
investigating language display issues. The theme editor menu pointer is 
completely separate from Content → Menus and is frequently overlooked.

---

### 3. Chinese Collection Page Filter Labels
Collection page filters (Availability, Price) displaying in Chinese 
(供货情况, 价格) despite English being the default language.

**Root Cause:** Previous developer had set custom Chinese override labels in 
Apps → Search & Discovery → Filters, overriding Shopify's default English 
system strings.

**Resolution:** Navigated to Apps → Search & Discovery → Filters → edited 
each filter label field back to English (Availability, Price).

---

### 4. Redundant & Poorly Structured Collections
Store had 12+ collections with multi-word descriptive names (Pearl Ring, 
Pearl Bracelet, Coin Pearl, Modern Bracelet, etc.) instead of a proper 
tag-based taxonomy system.

**Resolution:**
- Audited all collections and products (~4 hours)
- Deleted all redundant multi-word collections
- Rebuilt collection structure around 4 canonical categories
- Implemented single-word tag taxonomy
- Configured automated collection rules using tag filtering
- Confirmed Shopify collection rules are case-insensitive

---

### 5. Broken Navigation & Missing Pages
- Main menu contained broken links
- Contact page assigned wrong template (page instead of page.contact)
- Client personal Gmail hardcoded into contact page content
- Menu had typographical error ("Meun" instead of "Menu")

**Resolution:** Rebuilt navigation menu, reassigned contact page to 
page.contact template, removed personal email from page content editor.

---

### 6. Inconsistent Product Images
Mix of square 800x800 and portrait images at various aspect ratios causing 
misaligned collection grid rows.

**Resolution:** Audited entire product catalog. Identified and recropped 5-6 
irregular images. Established 1440x1920px portrait ratio as store standard.

---

## Implementation

### Theme Migration: Horizon → Dawn

1. Duplicated existing broken Horizon theme as backup
2. Installed fresh Horizon theme as unpublished sandbox for evaluation
3. Determined Horizon collection sections incompatible with requirements
4. Installed Dawn theme as unpublished draft
5. Configured Dawn to full MVP standard
6. Published Dawn — old themes auto-archived

**Dawn Theme Configuration:**
- Logo and favicon uploaded
- Announcement bar
- Hero banner
- 4-collection homepage with manual sort order
- Thumbnail carousel product gallery
- Testimonials section
- Language selector in header
- Store policies in footer
- Newsletter signup footer block

---

### Collection Architecture

**Previous structure (removed):**
12+ multi-word collections — Pearl Ring, Pearl Bracelet, Pearl Necklace, etc.

**New structure:**

| Collection | Handle | Rule Type | Rule |
|---|---|---|---|
| Rings | /collections/ring | Automated | Tag equals "ring" |
| Bracelets | /collections/bracelet | Automated | Tag equals "bracelet" |
| Earrings | /collections/earring | Automated | Tag equals "earring" |
| Necklaces | /collections/necklace | Automated | Tag equals "necklace" |

**Tag Taxonomy:** Single-word tags for all product attributes.
Examples: pearl, amber, turquoise, coin, disc, ring, bracelet, earring, 
necklace, modern, classic, gold, silver

**Note:** Shopify automated collection rules are case-insensitive. Tag 
normalization was determined unnecessary.

---

### Multilanguage & Internationalization

**Languages:** English (default), Chinese Simplified, Chinese Traditional, 
French, German, Spanish, Japanese, Korean, Portuguese, Hindi, Vietnamese

**Implementation:**
- Languages published via Settings → Languages
- Language selector enabled via Theme settings → Localization
- Geolocation - GLC app installed and enabled via App Embeds
- Geolocation provides automatic language/region suggestion based on visitor IP

**China Accessibility Note:** Shopify may be inaccessible from mainland China 
without VPN due to Great Firewall restrictions. Geolocation detection works 
correctly for all accessible regions.

**Translate & Adapt Note:** App was installed during language investigation 
and accidentally triggered German auto-translation. Confirmed not visible to 
customers as German was not assigned to any active market. App uninstalled 
after determining it was contributing to language display conflicts.

---

### Professional Email (Pending — Client Action Required)

**Recommendation:** QQ Mail (Tencent) with custom domain
- Target address: info@elynjewelry.com
- Accessible in China without VPN
- Integrates with existing QQ/WeChat ecosystem
- Free for personal accounts with domain email add-on
- Requires CNAME + MX DNS records added in Alibaba Cloud
- Client can use existing QQ account — no new account needed
- Setup instructions provided to client in English and Chinese

---

## Technical Investigation Log

| Issue | Time | Root Cause | Resolution |
|---|---|---|---|
| Chinese navbar on all pages | ~3 hrs | Theme referencing 主菜单 | Created English menu, redirected theme |
| Store defaulting to Chinese | ~1 hr | China-only market + Chinese menu | Menu fix resolved display |
| Chinese collection filter labels | ~30 min | Custom Chinese labels in Search & Discovery | Reset filter labels to English |
| Horizon collection display | ~1.5 hrs | Single-block template limitation | Migrated to Dawn |
| Translate & Adapt conflicts | ~1 hr | App causing language conflicts | Uninstalled |
| Markets configuration errors | ~1 hr | Basic plan — no multiple markets | Reverted, resolved via menu fix |
| Contact page 404 | ~15 min | Wrong page template | Reassigned to page.contact |

---

## Files & Settings Modified

| Location | Change |
|---|---|
| Locales/zh-CN.json | Commented to prevent Chinese locale override |
| Locales/zh-TW.json | Commented to prevent Chinese locale override |
| Content → Menus | Created English Main Menu, deprecated 主菜单 |
| Pages → Contact Us | Assigned page.contact template, removed personal email |
| Apps → Search & Discovery → Filters | Reset Availability and Price filter labels to English |
| Settings → General | Updated business address from China to international |

---

## Deliverables

- ✅ Functional international e-commerce store
- ✅ Clean professional Dawn v15.4.1 theme
- ✅ 4-collection homepage with manual sort order
- ✅ English navigation rebuilt from scratch
- ✅ 11-language support with geolocation detection
- ✅ Store policies (Privacy, Refund, Shipping, Terms of Service)
- ✅ Contact page with form (personal email removed)
- ✅ Favicon and logo
- ✅ Announcement bar
- ✅ Customer testimonials section
- ✅ Thumbnail carousel product image gallery
- ✅ Collection filter labels corrected to English
- ✅ Product image standardization across full catalog
- ✅ Automated collection taxonomy with single-word tag system
- ✅ Client handoff documentation (English)
- ⏳ Professional email setup info@elynjewelry.com (pending client Alibaba Cloud access)
- ⏳ 5th custom/personalization collection (pending client decision)
- ⏳ Product reviews system (recommended after real reviews collected)

---

## Recommendations for Client

### Immediate (Client Action Required)
1. Set up info@elynjewelry.com via QQ Mail — DNS records needed in Alibaba Cloud
2. Decide on 5th collection for custom/personalization jewelry
3. Retake product photos at 1440x1920px for remaining inconsistent images
4. All new product uploads should use single-word tags only

### Short Term
1. Enable product reviews once real customer reviews collected
2. Clean up unpublished Horizon theme drafts from theme library
3. Delete deprecated 主菜单 once confirmed unused by all themes

### Medium Term
1. Full Chinese translation via professional translation service
2. Instagram integration — high value for jewelry e-commerce
3. Blog setup for SEO content marketing
4. Google Analytics integration

### Long Term
1. WeChat Pay / Alipay integration for Chinese customer base
2. Consider Taobao/Tmall storefront for China-specific sales
3. Custom theme development for fully branded experience
4. Upgrade Shopify plan for proper international market configuration

---

## Market Value Reference

| Market | Estimated Project Value |
|---|---|
| United States | $2,000 — $4,000 USD |
| China | ¥8,000 — ¥18,000 RMB |
| Global Average | $2,500 — $5,000 USD |

*Includes store recovery, theme migration, inventory reorganization (~4hrs), 
internationalization setup, bug fixes, and client documentation.*

---

## Lessons Learned

1. **Check theme menu references first** when investigating language display 
   issues — the theme editor menu pointer is separate from Content → Menus
2. **Full store audit before touching anything** — 30 minutes of structured 
   investigation at project start would have revealed the Chinese market, 
   menus, Alibaba Cloud domain, and Search & Discovery filter overrides
3. **Check Search & Discovery filter labels** when collection page UI shows 
   wrong language — these are frequently overlooked custom overrides
4. **Horizon theme has collection display limitations** — block architecture 
   makes independent multi-collection configuration difficult without code
5. **Shopify Basic plan limits internationalization** — no multiple market 
   support affects language/region architecture decisions
6. **China-specific technical knowledge adds value** — Great Firewall, 
   Alibaba Cloud DNS, QQ Mail ecosystem, and WeChat communication all 
   require specialized knowledge that most western developers lack

---

*Report prepared by Frosty Solutions — frostycloud.net — March 2026*
