When I ask you to create any custom Shopify section, always follow my custom section format below.

You must create the section using Shopify Liquid, schema, CSS, and JS if required.

Main rules:

1. Always create a new Shopify section file.
2. Section file name should match the section name in kebab-case.
   Example: Banner With Text → banner-with-text.liquid
3. CSS asset file name should also match the section name.
   Example: banner-with-text.css
4. Always include CSS asset at the top:
   {{ 'section-name.css' | asset_url | stylesheet_tag }}

5. Always include this dynamic spacing structure:
   - Desktop margin top
   - Desktop margin bottom
   - Desktop padding top
   - Desktop padding bottom
   - Mobile padding top
   - Mobile padding bottom

6. Always use this scoped style format:

{%- style -%}
  @media screen and (min-width: 750px) {
    #shopify-section-{{ section.id }} {
      margin-top: {{ section.settings.margin_top }}px;
      margin-bottom: {{ section.settings.margin_bottom }}px;
    }
    .section-{{ section.id }}-padding {
      padding-top: {{ section.settings.padding_top }}px;
      padding-bottom: {{ section.settings.padding_bottom }}px;
    }
  }
  @media screen and (max-width: 749px) {
    .section-{{ section.id }}-padding {
      padding-top: {{ section.settings.padding_top_mobi }}px;
      padding-bottom: {{ section.settings.padding_bottom_mobi }}px;
    }
  }
{%- endstyle -%}

7. Main wrapper format should always be:

<div class="section-{{ section.id }} section-{{ section.id }}-padding section-{{ section.id }}-margin color-{{ section.settings.color_scheme }} gradient section-main-box CUSTOM-SECTION-CLASS">
  <!-- section content here -->
</div>

8. Replace `CUSTOM-SECTION-CLASS` with the section-specific wrapper class.
   Example:
   banner-with-text-main

9. Schema must always include:
   - name
   - class
   - tag: section
   - settings
   - presets

10. Schema class should match the section name wrapper.
    Example:
    "class": "banner-with-text-wrapper"

11. Always include this setting first:

{
  "type": "color_scheme",
  "id": "color_scheme",
  "label": "Color scheme",
  "default": "background-1"
}

12. Always include this desktop spacing group:

{
  "type": "header",
  "content": "Section Settings"
},
{
  "type": "range",
  "id": "padding_top",
  "min": 0,
  "max": 200,
  "step": 2,
  "unit": "px",
  "label": "Padding Top",
  "default": 0
},
{
  "type": "range",
  "id": "padding_bottom",
  "min": 0,
  "max": 200,
  "step": 2,
  "unit": "px",
  "label": "Padding Bottom",
  "default": 0
},
{
  "type": "range",
  "id": "margin_top",
  "min": 0,
  "max": 200,
  "step": 2,
  "unit": "px",
  "label": "Margin Top",
  "default": 0
},
{
  "type": "range",
  "id": "margin_bottom",
  "min": 0,
  "max": 200,
  "step": 2,
  "unit": "px",
  "label": "Margin Bottom",
  "default": 0
}

13. Always include this mobile spacing group:

{
  "type": "header",
  "content": "Section Settings For Mobile"
},
{
  "type": "range",
  "id": "padding_top_mobi",
  "min": 0,
  "max": 100,
  "step": 1,
  "unit": "px",
  "label": "Padding top",
  "default": 25
},
{
  "type": "range",
  "id": "padding_bottom_mobi",
  "min": 0,
  "max": 100,
  "step": 1,
  "unit": "px",
  "label": "Padding bottom",
  "default": 25
}

14. Add extra settings only based on the section requirement.
    Example:
    - image_picker for image
    - text for heading/button
    - richtext for description
    - url for button link
    - collection/product settings if needed
    - checkbox/select/range/color where useful

15. CSS must be created separately for the asset CSS file.
16. CSS format must be one-line per selector.
17. Each new CSS class should start from a new line.
18. Do not write CSS in traditional multi-line format.
19. CSS example format:

.banner-with-text-main { width: 100%; position: relative; }
.banner-with-text-main .banner-inner { display: flex; align-items: center; gap: 40px; }
.banner-with-text-main .banner-content { width: 50%; }

20. JavaScript should be added only if required.
21. If JavaScript is required, scope it inside the current section only using section id or wrapper class.
22. Do not affect other sections.
23. Use meaningful class names based on the section name.
24. Use Shopify dynamic settings instead of static content.
25. Make the section compatible with Dawn theme.
26. Always give me ready-to-paste full code.
27. Clearly separate:
    - Section Liquid code
    - CSS file code
    - JS code if needed
28. Do not skip schema.
29. Do not remove my spacing structure.
30. Do not change my one-line CSS format.

When I say “create custom section”, use this full format automatically.