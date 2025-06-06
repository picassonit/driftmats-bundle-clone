# Installation Guide

## Quick Start (5 minutes)

### Step 1: Download the Snippet
Download the `driftmats-bundle.liquid` file from this repository.

### Step 2: Upload to Shopify
1. Go to your Shopify admin panel
2. Navigate to **Online Store > Themes**
3. Find your active theme and click **Actions > Edit code**
4. In the left sidebar, locate the **Snippets** folder
5. Click **Add a new snippet**
6. Name it `driftmats-bundle`
7. Paste the entire contents of the downloaded file
8. Click **Save**

### Step 3: Add to Product Page
Find your product template (usually `sections/product-form.liquid` or `templates/product.liquid`) and add this line where you want the bundle to appear:

```liquid
{% render 'driftmats-bundle', product: product %}
```

### Step 4: Save and Test
1. Save your template file
2. Visit any product page on your store
3. You should see the bundle selector with 3 options

## Detailed Installation

### For Dawn Theme (Shopify's default)

1. **Edit the product form section**:
   - Go to `sections/product-form.liquid`
   - Find the quantity selector (around line 45-60)
   - Add the bundle render tag before or after it:

```liquid
<div class="product-form__quantity">
  <!-- Existing quantity selector -->
</div>

<!-- Add bundle here -->
{% render 'driftmats-bundle', product: product %}

<div class="product-form__buttons">
  <!-- Existing add to cart button -->
</div>
```

### For Debut Theme

1. **Edit the product template**:
   - Go to `sections/product-template.liquid`
   - Find the product form area (around line 200-250)
   - Add the bundle render tag:

```liquid
<div class="product-single__add-to-cart">
  <!-- Existing price and quantity -->
  
  <!-- Add bundle here -->
  {% render 'driftmats-bundle', product: product %}
  
  <!-- Existing add to cart button -->
</div>
```

### For Brooklyn Theme

1. **Edit the product form**:
   - Go to `templates/product.liquid`
   - Find the form section (around line 150-200)
   - Add the bundle render tag:

```liquid
<form action="/cart/add" method="post" enctype="multipart/form-data">
  <!-- Existing form content -->
  
  <!-- Add bundle before submit button -->
  {% render 'driftmats-bundle', product: product %}
  
  <div class="btn-wrapper">
    <!-- Existing submit button -->
  </div>
</form>
```

### For Custom Themes

If you have a custom theme, look for these common files:
- `sections/product-form.liquid`
- `templates/product.liquid`
- `snippets/product-form.liquid`
- `sections/product.liquid`

The bundle should be added in the product form area, typically:
- After the price display
- Before or after the quantity selector
- Before the add to cart button

## Placement Options

### Option 1: Replace quantity selector
If you want the bundle to replace the default quantity selector:

```liquid
<!-- Comment out or remove existing quantity selector -->
{% comment %}
<div class="product-form__quantity">
  <!-- quantity input -->
</div>
{% endcomment %}

<!-- Add bundle instead -->
{% render 'driftmats-bundle', product: product %}
```

### Option 2: Add as separate section
Create a new section file `sections/product-bundle.liquid`:

```liquid
{% render 'driftmats-bundle', product: product %}

{% schema %}
{
  "name": "Product Bundle",
  "tag": "section",
  "class": "section",
  "settings": []
}
{% endschema %}
```

Then add it to your product template:

```liquid
{% section 'product-bundle' %}
```

### Option 3: Theme customizer
Some themes allow adding custom code through the theme customizer:

1. Go to **Online Store > Themes > Customize**
2. Navigate to a product page
3. Look for "Custom Code" or "HTML" blocks
4. Add the render tag there

## Testing Checklist

After installation, verify:

- [ ] Bundle appears on product pages
- [ ] All 3 options are visible
- [ ] "MOST POPULAR" badge shows on 2-pack
- [ ] "BEST VALUE" badge shows on 3-pack
- [ ] Prices calculate correctly with discounts
- [ ] Free gift text displays
- [ ] Radio buttons work when clicking options
- [ ] Add to cart button updates price
- [ ] Products actually add to cart
- [ ] Bundle works on mobile devices

## Troubleshooting

### Bundle not appearing?
- Check the file is saved in `snippets/` folder
- Verify the filename is exactly `driftmats-bundle.liquid`
- Make sure you're on a product page (not collection/home page)
- Check the render syntax: `{% render 'driftmats-bundle', product: product %}`

### Styling looks broken?
- Your theme might have conflicting CSS
- Try adding `!important` to key styles
- Check browser developer tools for CSS conflicts
- The bundle is designed to work in a 400px width container

### JavaScript errors?
- Check browser console for errors
- Ensure your theme loads jQuery (if it uses jQuery)
- Some themes modify the cart API - check compatibility

### Prices not calculating?
- Verify the product has a price set
- Check if your theme uses a different currency format
- The snippet uses `money_without_currency` filter

## Advanced Configuration

### Multiple products
To use the bundle on specific products only:

```liquid
{% if product.handle == 'your-product-handle' %}
  {% render 'driftmats-bundle', product: product %}
{% endif %}
```

### Product type filtering
To show bundles only for certain product types:

```liquid
{% if product.type == 'Bundle Products' %}
  {% render 'driftmats-bundle', product: product %}
{% endif %}
```

### Collection-based
To show bundles only for products in a specific collection:

```liquid
{% assign bundle_collection = collections['bundle-products'] %}
{% if bundle_collection.products contains product %}
  {% render 'driftmats-bundle', product: product %}
{% endif %}
```

## Support

If you encounter issues:

1. Double-check the installation steps
2. Review the troubleshooting section
3. Check the [README.md](README.md) for additional details
4. Create an issue in this repository with:
   - Your theme name
   - Steps you followed
   - Error messages or screenshots
   - Browser and device information