# PRSNTSTUATN — theme 1.1

An original Shopify Online Store 2.0 theme for an object-led gift house. The design uses a blonde background (`#F3EDDE`), khaki details (`#8B8F72`) and russet (`#874016`), generous space, serif editorial headings and restrained navigation.

**Every relationship has a present situation.** Present as a gift; present as a moment in time.

## Review and install in Shopify

1. Use `dist/PRSNTSTUATN-theme.zip` (or run `npm run package` to regenerate it).
2. In Shopify admin, go to **Online Store → Themes → Add theme → Upload zip file**. This adds an unpublished theme; it does not replace your live theme.
3. Open **Customize** for the uploaded theme. Review desktop and mobile before publishing.
4. Under **Theme settings → Brand & colors**, adjust the display name, subtitle and colors.
5. In **Featured collection**, choose a real Shopify collection. The theme then uses your real titles, images, prices and product links. Until a collection is selected, the homepage shows clearly marked illustrative collection previews with no invented prices or purchase controls.
6. Set the header navigation menu and footer client-care menu. The default category labels lead to all products until you assign your own menu. Create collections and menu links for your actual gift categories.
7. Replace the editorial hero and story images through their section image pickers, or retain the supplied original concept imagery. Add alt text to uploaded images. All copy is editable in the sections.
8. Add your shipping, returns and privacy policies in Shopify settings, and connect them through the footer menu. The theme also displays available Shopify policies by default.
9. Confirm payment, shipping, taxes, currency, market and email settings in Shopify. Place a Shopify test order and test newsletter registration in the **unpublished theme preview** before launch. Publish only when you are satisfied.

The generated editorial photograph and original vector studies are concept imagery, not representations of your real inventory. There are no third-party brand logos or reference-site assets in this theme. No Shopify account is connected, no live store has been changed, and no real order, payment or subscription has been tested here.

## Version 1.1 setup

This update adds a right-side bag drawer, an image-led Products mega menu, the supplied logo prepared with a transparent background (russet header / blonde footer), About and Why pages, a Shopify contact form, editable FAQs, social icons, and reduced-motion-aware transitions. Upload this ZIP as a **new unpublished theme** so you can preserve your existing theme and settings while reviewing.

Create the following pages in **Online Store → Pages** and assign the theme templates shown below. Shopify theme files cannot create store content automatically. If the new templates do not appear in the admin template picker while this theme is unpublished, preview/assign them through your store’s supported theme workflow before launch; avoid changing the live theme just to test.

| Page title | URL handle | Theme template |
| --- | --- | --- |
| About us | `about-us` | `about` |
| Contact us | `contact-us` | `contact` |
| Why us | `why-us` | `why` |
| FAQs | `faqs` | `faq` |
| Terms and conditions | `terms-and-conditions` | `terms` |

Home and Products use the native home and collection templates. Customize the About, Why, and Contact copy in the theme editor. FAQ questions and answers are editable section blocks. Add your **actual approved terms** to the Terms page body, or configure Shopify’s Terms of Service policy; the footer prefers the native policy URL when one exists. The theme does not invent legal terms, shipping promises, social profile URLs, or store policies.

Under **Theme settings → Social media**, enter your Instagram, Pinterest and Facebook profile URLs. Until a URL is supplied, its icon is decorative, not a dead link. Product mega-menu images and captions are editable under Header; assigning a Shopify product menu replaces the default category links.

### Customer accounts

The account icon and footer/mobile account links use Shopify’s native customer login route. Enable **new customer accounts** in Shopify admin to use email verification sign-in. Enable/configure Google as an available sign-in provider in your Shopify customer account authentication settings where supported. Google provider setup may require store-admin access and provider credentials; enter those only in the supported Shopify/Google setup, never in the theme or chat. The theme itself does not collect passwords or fabricate a Google login flow. Sign-in, contact delivery, newsletter delivery and checkout must be tested on the real store. This environment has no authenticated Shopify admin connection.

### Motion and accessibility

The bag uses a native modal dialog for keyboard focus containment, Escape/backdrop dismissal and focus restoration. Quantity adjustments use Shopify’s cart API and the drawer is re-rendered by Shopify’s section-rendering endpoint, preserving native currency formatting and server pricing. Cart errors offer a working full-bag fallback. The product menu supports keyboard, click and desktop mouse entry, with ease-in/ease-out opening and closing. A reduced-motion preference disables animations. Without JavaScript, the bag link still opens Shopify’s cart page and menu disclosures remain usable.

## Local development

Use the existing checkout at `/workspace/prsntstuatn`. Each cloud task is already isolated; no extra Git worktree is needed.

Requires Node 22.12+ (Node 24 was used), npm, Python 3 for ZIP packaging, and Chromium for browser checks.

```sh
npm ci --cache /tmp/prsntstuatn-npm
npm run check
npm run preview
```

The local renderer listens on port 3000, adjustable using `PORT`. It renders the same Liquid sections with LiquidJS and a clearly labeled **sample** catalog. It is for design review and browser interaction testing. It is not a substitute for Shopify's Liquid runtime. Sample prices use USD only for demonstration; the real theme uses Shopify's money filter and configured currency. Preview baskets are isolated by session and reset when the local renderer restarts.

```sh
npm test
npm run package
```

`npm test` starts its own renderer on port 3100. It checks page rendering, automated WCAG checks, mobile navigation, search, sorting, variant selection, sold-out behavior, successful/failed add-to-bag, quantity updates, item removal, image loading and responsive overflow. It saves desktop and mobile screenshots in `dist/`. It uses `/usr/bin/chromium`; set `CHROMIUM_PATH` for another installed browser. Automated accessibility checks do not establish full accessibility compliance; manual keyboard and assistive technology review remains useful.

`npm run check` runs Shopify's official Theme Check. `npm run package` includes only supported Shopify theme directories, not local scripts, sample data, development dependencies or screenshots.

For authoritative store rendering after you have Shopify CLI access:

```sh
npx shopify theme dev --store YOUR-STORE.myshopify.com
```

Authenticate through Shopify's supported login flow. Never put credentials in source files or chat. Local theme checking and ZIP creation require no store credentials. Live checkout, inventory enforcement, pagination, policy pages, market localization and newsletter delivery must be verified on Shopify.

## Theme structure

- `layout/theme.liquid`: shared accessible layout.
- `sections/`: editable homepage, navigation, footer and commerce templates.
- `templates/`: native JSON templates for home, product, collection, collection list, cart, search, content page and 404.
- `snippets/`: product card and original interface icons.
- `assets/`: responsive CSS, progressive JavaScript, original generated hero photograph and original illustrative SVGs.
- `scripts/`: local-only sample renderer, browser checks and ZIP packager; not uploaded to Shopify.

Shopping uses native Shopify product forms and cart endpoints. JavaScript progressively enhances product additions and variant prices; forms and ordinary links remain usable without it. Newsletter submissions use Shopify's native customer form. No external fonts, storefront tokens, paid libraries or API credentials are required by the theme.
