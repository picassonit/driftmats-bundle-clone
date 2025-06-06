# DriftMats Bundle Clone

An exact replica of DriftMats' bundle functionality using Shopify Liquid. This implementation clones the "Kaching Bundles" app styling and behavior without requiring any third-party apps.

## Features

✅ **Exact Visual Match**: Replicates DriftMats' bundle design pixel-perfect  
✅ **Bundle Options**: 1-pack, 2-pack (Most Popular), 3-pack (Best Value)  
✅ **Discount Logic**: 10% off 2-pack, 12% off 3-pack  
✅ **Free Gifts**: $5 Gift Card (2-pack), Wall Needles (3-pack)  
✅ **Responsive Design**: Works on all screen sizes  
✅ **Shopify Integration**: Native cart API integration  
✅ **No Dependencies**: Pure Liquid, CSS, and vanilla JavaScript  

## Bundle Configuration

| Pack Size | Discount | Badge | Free Gift |
|-----------|----------|-------|----------|
| 1 pack | None | - | - |
| 2 pack | 10% | MOST POPULAR | + FREE $5 Gift Card |
| 3 pack | 12% | BEST VALUE | + FREE Needles for the Wall |

## Styling Details

- **Title**: "BUNDLE & SAVE" (20px bold)
- **Layout**: Vertical bundle options
- **Corner Radius**: 8px
- **Background**: rgba(143,143,143,0.07)
- **Selected Background**: White
- **Border Color**: Red (#ff0000)
- **Badge Styling**: Red background, white text
- **Fonts**: System fonts with 14px bold titles

## Installation

### Method 1: Direct File Upload

1. Download `snippets/driftmats-bundle.liquid`
2. In your Shopify admin, go to **Online Store > Themes**
3. Click **Actions > Edit code** on your active theme
4. In the **Snippets** folder, click **Add a new snippet**
5. Name it `driftmats-bundle` and paste the code
6. Save the file

### Method 2: Theme Customizer

1. Copy the contents of `snippets/driftmats-bundle.liquid`
2. Add it as a new snippet in your theme
3. Use the installation code below in your product template

## Usage

### In Product Templates

Add this line to your product template where you want the bundle to appear:

```liquid
{% render 'driftmats-bundle', product: product %}
```

### Common Locations

**Product Page (product.liquid or product-form.liquid)**:
```liquid
<div class="product__info">
  <!-- Existing product info -->
  <div class="product__price">
    <!-- Price display -->
  </div>
  
  <!-- Add bundle here -->
  {% render 'driftmats-bundle', product: product %}
  
  <div class="product__buttons">
    <!-- Regular add to cart button -->
  </div>
</div>
```

**Product Form Section**:
```liquid
{% comment %} Add before or after the quantity selector {% endcomment %}
{% render 'driftmats-bundle', product: product %}
```

## Customization

### Change Colors

Update these CSS variables in the snippet:

```css
/* Bundle border and badges */
border-color: #ff0000; /* Change to your brand color */

/* Badge background */
background: #ff0000; /* Change to your brand color */

/* Add to cart button */
background: #ff0000; /* Change to your brand color */
```

### Modify Discounts

Update the discount calculations in the Liquid code:

```liquid
<!-- For 2-pack (currently 10% off) -->
{% assign discounted_price = product_price | times: 2 | times: 0.9 %}

<!-- For 3-pack (currently 12% off) -->
{% assign discounted_price_3 = product_price | times: 3 | times: 0.88 %}
```

### Change Free Gifts

Modify the gift text in the HTML:

```liquid
<div class="free-gift">
  <span class="gift-text">+ FREE Your Custom Gift</span>
</div>
```

## Browser Support

- ✅ Chrome/Edge 60+
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Mobile browsers
- ✅ Shopify's mobile app

## Performance

- **Zero Dependencies**: No external libraries
- **Lightweight**: < 5KB total size
- **Fast Loading**: Inline CSS and JavaScript
- **SEO Friendly**: Semantic HTML structure

## Troubleshooting

### Bundle not showing?
1. Check that the snippet is saved in the `snippets` folder
2. Verify the render tag syntax: `{% render 'driftmats-bundle', product: product %}`
3. Ensure you're on a product page with a valid product object

### Styling issues?
1. Check for CSS conflicts with your theme
2. Add `!important` to critical styles if needed
3. Inspect element to see which styles are being overridden

### Cart not updating?
1. Verify your theme supports the Shopify AJAX Cart API
2. Check browser console for JavaScript errors
3. Test with a simple product first

## Support

This is an open-source implementation. For customizations or issues:

1. Check the [Issues](../../issues) tab
2. Review the troubleshooting section above
3. Submit a detailed bug report with:
   - Shopify theme name
   - Browser and version
   - Console error messages
   - Screenshots if applicable

## License

MIT License - Feel free to use and modify for your projects.

## Credits

Based on the design and functionality of DriftMats' bundle implementation using the "Kaching Bundles" Shopify app.