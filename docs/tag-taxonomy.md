# docs/tag-taxonomy.md

# Product Tag Taxonomy
# Jewelry E-Commerce Store

**Prepared by:** Frosty Solutions  
**Website:** frostycloud.net  
**Date:** March 2026  

---

## Overview

This store uses an automated collection system driven by product tags.
When you add a product and assign the correct tags, it automatically 
appears in the correct collection on the website. No manual collection 
assignment is needed.

This document defines the tag system and how to use it correctly.

---

## How Tags Work

1. You add a new product in Shopify admin
2. You add tags to the product (e.g. ring, pearl, gold)
3. Shopify automatically checks all collection rules
4. The product appears in the matching collection immediately
5. No further action required

---

## Collection Rules

These are the automated rules currently configured:

| Collection | Tag Required | URL |
|---|---|---|
| Rings | ring | /collections/ring |
| Bracelets | bracelet | /collections/bracelet |
| Earrings | earring | /collections/earring |
| Necklaces | necklace | /collections/necklace |

**Important:** Tags are case-insensitive. "Ring", "ring", and "RING" 
all work the same way. However using lowercase is recommended for 
consistency.

---

## Full Tag Reference

### Category Tags (Required)
Every product must have at least one category tag.

| Tag | Use For |
|---|---|
| ring | All ring products |
| bracelet | All bracelet products |
| earring | All earring products |
| necklace | All necklace products |

---

### Material Tags (Recommended)
Add material tags to improve search and SEO.

| Tag | Use For |
|---|---|
| pearl | Products featuring pearls |
| gold | Gold colored or gold plated items |
| silver | Silver colored or silver plated items |
| amber | Products featuring amber stones |
| turquoise | Products featuring turquoise stones |
| diamond | Products featuring diamonds |
| crystal | Products featuring crystals |
| jade | Products featuring jade |

---

### Style Tags (Optional)
Add style tags for better filtering and searchability.

| Tag | Use For |
|---|---|
| modern | Contemporary modern design |
| classic | Traditional classic design |
| minimalist | Simple minimal design |
| statement | Bold statement pieces |
| delicate | Fine delicate pieces |
| vintage | Vintage inspired design |

---

### Shape Tags (Optional)

| Tag | Use For |
|---|---|
| coin | Coin shaped elements |
| disc | Disc shaped elements |
| heart | Heart shaped elements |
| flower | Flower shaped elements |
| chain | Chain style pieces |

---

### Custom/Special Tags (Future Use)

| Tag | Use For |
|---|---|
| custom | Custom/personalization products |
| bestseller | Top selling products |
| new | Newly added products |
| sale | Products on sale |
| gift | Products suitable as gifts |

---

## Tag Examples

**Pearl Ring:**
```
ring, pearl
```

**Gold Bracelet:**
```
bracelet, gold
```

**Pearl and Amber Necklace:**
```
necklace, pearl, amber
```

**Modern Minimalist Earrings:**
```
earring, modern, minimalist
```

**Custom Diamond Ring:**
```
ring, diamond, custom
```

---

## Rules for Adding Tags

1. **Always use single words** — never use multi-word tags like 
   "pearl bracelet" or "gold ring"
2. **Always include at least one category tag** — ring, bracelet, 
   earring, or necklace
3. **Use lowercase** — for consistency across the store
4. **Separate tags with commas** in the Shopify tag field
5. **Do not create new collection tags** without updating the 
   collection rules in Shopify admin

---

## How to Add Tags to a Product

1. Go to **Products** in Shopify admin
2. Click the product
3. Find the **Tags** field on the right side of the page
4. Type each tag and press **Enter** or **comma** to add it
5. Add all relevant tags
6. Click **Save**

---

## How to Add Tags in Bulk

To add a tag to multiple products at once:

1. Go to **Products** in Shopify admin
2. Select multiple products using the checkboxes
3. Click **Actions → Add tags**
4. Type the tag and confirm
5. All selected products will receive that tag

---

## Common Mistakes to Avoid

- Using multi-word tags (e.g. "pearl ring" instead of "pearl" and "ring")
- Forgetting the category tag — product will not appear in any collection
- Using inconsistent spelling (e.g. "earrings" instead of "earring")
- Creating duplicate tags with different spellings
- Using spaces inside tags

---

## Adding a New Collection in Future

If a new collection is needed (e.g. Custom Jewelry):

1. Go to **Products → Collections → Create collection**
2. Name the collection
3. Set rule: **Product tag is equal to** → enter the new tag
4. Save the collection
5. Add the new collection to the homepage in the theme editor
6. Update this tag taxonomy document with the new tag

---

*Document prepared by Frosty Solutions — frostycloud.net — March 2026*
