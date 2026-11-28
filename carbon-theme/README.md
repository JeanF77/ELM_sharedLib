# carbon-theme

Tokens of the IBM Carbon Design System as CSS custom properties (`--cds-*`),
for the widgets that have no build step.

| File | Content |
|---|---|
| `11.85.0/carbon-theme-g10.css` | Theme Gray 10: colors (theme, contextual and component tokens), spacing, sizes, border radius, type |
| `11.85.0/LICENSE` | Apache-2.0 license of the Carbon packages |
| `generate_carbon_theme.py` | Generator of the CSS file |

The CSS file is generated, not written by hand. Its values come from the npm
packages `@carbon/themes` 11.85.0 (values already resolved in
`scss/generated/`), `@carbon/layout` 11.63.0 and `@carbon/type` 11.71.0:

```
curl -O https://registry.npmjs.org/@carbon/themes/-/themes-11.85.0.tgz
curl -O https://registry.npmjs.org/@carbon/layout/-/layout-11.63.0.tgz
curl -O https://registry.npmjs.org/@carbon/type/-/type-11.71.0.tgz
mkdir themes layout type
tar xzf themes-11.85.0.tgz -C themes; tar xzf layout-11.63.0.tgz -C layout; tar xzf type-11.71.0.tgz -C type
python3 generate_carbon_theme.py themes/package layout/package type/package g10 11.85.0/carbon-theme-g10.css
```

Another theme (`white`, `g90`, `g100`) or version gives another file, in a
folder named after the version of `@carbon/themes`.

Use it with the IBM Plex Sans font (`../ibm-plex-sans/1.1.0`):

```html
<link rel="stylesheet" href="../ELM_sharedLib/ibm-plex-sans/1.1.0/css/ibm-plex-sans-default.min.css">
<link rel="stylesheet" href="../ELM_sharedLib/carbon-theme/11.85.0/carbon-theme-g10.css">
```

then, in the widget's own stylesheet, `var(--cds-interactive)`,
`var(--cds-layer-01)`, `var(--cds-font-family-sans)`... The font families
(`--cds-font-family-sans`, `--cds-font-family-mono`) are not Carbon tokens:
the generator names them for convenience.
