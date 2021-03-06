---
label: Themes are used to customize component styles to fit the specific aesthetic of a brand or product.
title: Themes
---

## Resources

<grid-wrapper col_lg="8" flex="true" bleed="true">
<clickable-tile
    title="Theming sandbox"
    href="http://themes.carbondesignsystem.com/"
    type="resource"
    >
    <img src="images/sandbox-icon.png" alt="Theming sandbox" />
</clickable-tile>
</grid-wrapper>


<anchor-links>
<ul>
    <li><a href="#theming-basics">Theming basics</a></li>
    <li><a href="#customizing-a-theme">Customizing a theme</a></li>
    <li><a href="#tokens">Tokens</a></li>
    <li><a href="#theming-applied">Theming applied</a></li>
</ul>
</anchor-links>

## Theming basics

Themes are used to modify existing components to fit a specific visual style. By using Carbon's tokens, developers can easily customize all of their components by changing a set of universal variables, eliminating the need to modify individual components.

### Theme terms

| Term      | Definition                                                                                                  |
| --------- | ----------------------------------------------------------------------------------------------------------- |
| **Theme** | The set of unique values assigned to the system's tokens                                                            |
| **Token** | The code identifier for a unique role or set of roles. Tokens are universal and never change across themes. |
| **Role**  | The systematic usage/s of a token. Roles cannot be changed between themes.                                  |
| **Value** | The actual style (i.e. hex code) assigned to a token                                                         |

### Default theme

Carbon's default theme (White theme) is based on the IBM Design Language. When `carbon-components` is downloaded and installed, the components are preset to use the default theme.

<grid-wrapper col_lg="8" flex="true" bleed="true">
<clickable-tile
    title="Carbon themes"
    href="https://github.com/carbon-design-system/carbon-themes"
    type="resource"
    >
    <img src="images/github-icon.png" alt="Theming repo" />
</clickable-tile>
</grid-wrapper>

## Customizing a theme

The default theme acts as a starting point; from there designers and developers can define how their own components and styles deviate from the default. Altering one, some, or all of the default token values will result in a new theme. The developer then packages those new values into a new theme scss stylesheet which will replace the values of the default theme:

1. Create a theme mixin that effectively mimics this structure, but changes up hex values as needed:

        @mixin theme-white {
          $interactive-01: #0062ff !default !global;
          $interactive-02: #171717 !default !global;
          $interactive-03: #0062ff !default !global;
          $ui-background: #ffffff !default !global;
          $ui-01: #f3f3f3 !default !global;
          $ui-02: #ffffff !default !global;
          $ui-03: #dcdcdc !default !global;
          $ui-04: #8c8c8c !default !global;
          $ui-05: #171717 !default !global;
          $text-01: #171717 !default !global;
          $text-02: #565656 !default !global;
          $text-03: #8c8c8c !default !global;
          $text-04: #ffffff !default !global;
          $icon-01: #171717 !default !global;
          $icon-02: #565656 !default !global;
          $field-01: #f3f3f3 !default !global;
          $field-02: #ffffff !default !global;
          $inverse-01: #ffffff !default !global;
          $inverse-02: #3d3d3d !default !global;
          $support-01: #da1e28 !default !global;
          $support-02: #198038 !default !global;
          $support-03: #fdd13a !default !global;
          $support-04: #054ada !default !global;
          $overlay-01: rgba(23, 23, 23, 0.5) !default !global;
          $focus: #0062ff !default !global;
          $hover-primary: #0353e9 !default !global;
          $active-primary: #0530ad !default !global;
          $hover-primary-text: #054ada !default !global;
          $hover-secondary: #4c4c4c !default !global;
          $active-secondary: #6f6f6f !default !global;
          $hover-tertiary: #0353e9 !default !global;
          $active-tertiary: #0530ad !default !global;
          $hover-ui: #e5e5e5 !default !global;
          $active-ui: #bebebe !default !global;
          $selected-ui: #dcdcdc !default !global;
          $hover-selected-ui: #cacaca !default !global;
          $hover-danger: #ba1b23 !default !global;
          $active-danger: #750e13 !default !global;
          $hover-row: #e5e5e5 !default !global;
          $visited-link: #8a3ffc !default !global;
          $disabled-01: #f3f3f3 !default !global;
          $disabled-02: #bebebe !default !global;
          $disabled-03: #8c8c8c !default !global;
          $brand-01: #0062ff !default !global;
          $brand-02: #171717 !default !global;
          $brand-03: #0062ff !default !global;
          $active-01: #bebebe !default !global;
          $hover-field: #e5e5e5 !default !global;
        }

2. Name the mixin (i.e., instead of `theme-white`, choose a unique name)

3. `@include UNIQUE-THEME-MIXIN();` in your scss, before importing component scss, etc. 

Alternatively, for relatively minor changes to an existing theme, a developer can make changes on a per-token basis. For example, after importing an existing Carbon theme, she could just set something like `$interactive-01: hotpink;`.

## Tokens

With tokens, the code only needs to be changed in one place to see the effect system-wide. Tokens are used across all components and help keep global patterns and styles consistent.

All tokens come pre-baked into the Carbon component source code. Tokens are denoted by the prefix `$` (e.g. `$ui-01`). Tokens can also be nested within other tokens. For example, `$interactive-01` calls the IBM Design Language color palette token `$ibm-color__blue--60` for its value in the default theme.

There are several token categories:

- color
- spacing
- typography
- global

### Color

Each theme is assigned 38 universal color variables, which are determined by [common roles and usage](/guidelines/color/usage). This allows for uniform color application across themes while maintaining full styling flexibility.

```scss
//// _color-tokens
// White Theme tokens
$interactive-01: $ibm-colors__blue--60 !default !global;
$interactive-02: $ibm-colors__blue--60 !default !global;
$ui-01: $ibm-colors__gray--10 !default !global;
$ui-02: $ibm-colors__white !default !global;
$ui-03: $ibm-colors__gray--20 !default !global;
$ui-04: $ibm-colors__gray--50 !default !global;
$ui-05: $ibm-colors__gray--100 !default !global;
$icon-01: $ibm-colors__gray--100 !default !global;
$icon-02: $ibm-colors__gray--70 !default !global;
$text-01: $ibm-colors__gray--100 !default !global;
$text-02: $ibm-colors__gray--70 !default !global;
$text-03: $ibm-colors__gray--50 !default !global;
$inverse-01: $ibm-colors__gray--10 !default !global;
$inverse-02: $ibm-colors__gray--80 !default !global;
$field-01: $ibm-colors__gray--10 !default !global;
$field-02: $ibm-colors__white !default
$support-01: $ibm-colors__red--60 !default !global;
$support-02: $ibm-colors__green--60 !default !global;
$support-03: $ibm-colors__yellow !default !global;
$support-04: $ibm-colors__blue--70 !default !global;
$overlay-01: rgba(255, 255, 255, 6) !default !global;
$overlay-02: rgba(23, 23, 23, 7) !default !global;

// Interaction tokens
$focus: $ibm-colors__blue--60 !default !global;
$hover-primary: #0353E9 !default !global;
$hover-primary-text: $ibm-colors__blue--70 !default !global; !default !global;
$hover-secondary: #6f6f6f !default !global;
$hover-ui: #e5e5e5 !default !global;
$hover-danger: #ba1b23 !default !global;
$hover-row: #e5e5e5 !default !global;
$active-primary: $ibm-colors__blue--80 !default !global; !default !global;
$active-secondary: $ibm-colors__gray--60 !default !global;
$active-ui: $ibm-colors__gray--30 !default !global;
$active-danger: $ibm-colors__red--80 !default !global;
$selected-ui: $ibm-colors__gray--20 !default !global;
$visited-link: $ibm-colors__purple--60 !default !global;
$disabled-01: $ibm-colors__gray--10 !default !global;
$disabled-02: $ibm-colors__gray--30 !default !global;
$disabled-03: $ibm-colors__gray--50 !default !global;
```

### Spacing

Carbon has two spacing scales, one for general spacing within components and the other for layout spacing. Both are designed to complement the components and typography throughout the system. Each scale has its own [distinct purpose](/guidelines/spacing). The two scales have certain overlapping values that serve two different roles, so be mindful when choosing a spacing token.

```scss
//// _spacing
$spacing-baseline: 1rem !default;

// Spacing scale
$spacing-4xs: $spacing-baseline * 0.0625 !default;
$spacing-3xs: $spacing-baseline * 0.125 !default;
$spacing-2xs: $spacing-baseline * 0.25 !default;
$spacing-xs: $spacing-baseline * 0.5 !default;
$spacing-sm: $spacing-baseline * 0.75 !default;
$spacing-md: $spacing-baseline !default;
$spacing-lg: $spacing-baseline * 1.5 !default;
$spacing-xl: $spacing-baseline * 2 !default;
$spacing-2xl: $spacing-baseline * 2.5 !default;
$spacing-3xl: $spacing-baseline * 3 !default;

// Layout scale
$layout-2xs: $spacing-baseline !default;
$layout-xs: $spacing-baseline * 1.5 !default;
$layout-sm: $spacing-baseline * 2 !default;
$layout-md: $spacing-baseline * 3 !default;
$layout-lg: $spacing-baseline * 4 !default;
$layout-xl: $spacing-baseline * 6 !default;
$layout-2xl: $spacing-baseline * 10 !default;
```

### Typography

Typography has four categories of type styles (universal, productive, editorial, and additional) that can be customized through tokens. These tokens are used both within components and across layouts. Type tokens are determined by their [role](/guidelines/typography/productive) across the system.

```scss
// Universal
$caption-01: (
  font-family: font-family('sans'),
  font-size: type-scale(1),
  font-weight: font-weight('regular'),
  line-height: rem(16px),
  letter-spacing: 0.32px,
) !default;

$label-01: (
  font-family: font-family('sans'),
  font-size: type-scale(1),
  font-weight: font-weight('regular'),
  line-height: rem(16px),
  letter-spacing: 0.32px,
) !default;

$helper-text-01: (
  font-family: font-family('sans'),
  font-size: type-scale(1),
  font-style: italic,
  line-height: rem(16px),
  letter-spacing: 0.32px,
) !default;

$body-short-01: (
  font-family: font-family('sans'),
  font-size: type-scale(2),
  font-weight: font-weight('regular'),
  line-height: rem(18px),
  letter-spacing: 0.16px,
) !default;

$body-long-01: (
  font-family: font-family('sans'),
  font-size: type-scale(2),
  font-weight: font-weight('regular'),
  line-height: rem(20px),
  letter-spacing: 0.16px,
) !default;

$body-short-02: (
  font-family: font-family('sans'),
  font-size: type-scale(3),
  font-weight: font-weight('regular'),
  line-height: rem(22px),
  letter-spacing: 0,
) !default;

$body-long-02: (
  font-family: font-family('sans'),
  font-size: type-scale(3),
  font-weight: font-weight('regular'),
  line-height: rem(24px),
  letter-spacing: 0,
) !default;

$code-01: (
  font-family: font-family('mono'),
  font-size: type-scale(1),
  font-weight: font-weight('regular'),
  line-height: rem(16px),
  letter-spacing: 0.32px,
) !default;

$code-02: (
  font-family: font-family('mono'),
  font-size: type-scale(2),
  font-weight: font-weight('regular'),
  line-height: rem(20px),
  letter-spacing: 0.32px,
) !default;

$heading-01: (
  font-family: font-family('sans'),
  font-size: type-scale(2),
  font-weight: font-weight('semibold'),
  line-height: rem(18px),
  letter-spacing: 0.16px,
) !default;

$heading-02: (
  font-family: font-family('sans'),
  font-size: type-scale(3),
  font-weight: font-weight('semibold'),
  line-height: rem(22px),
  letter-spacing: 0,
) !default;

$heading-03: (
  font-family: font-family('sans'),
  font-size: type-scale(5),
  font-weight: font-weight('regular'),
  line-height: rem(26px),
  letter-spacing: 0,
) !default;
```

```scss
// Productive
$productive-heading-04: (
  font-family: font-family('sans'),
  font-size: type-scale(6),
  font-weight: font-weight('regular'),
  line-height: rem(30px),
  letter-spacing: 0,
) !default;

$productive-heading-05: (
  font-family: font-family('sans'),
  font-size: type-scale(8),
  font-weight: font-weight('regular'),
  line-height: rem(40px),
  letter-spacing: 0,
) !default;
```

```scss
// Expressive
$expressive-heading-04: (
  font-family: font-family('sans'),
  font-size: type-scale(5),
  font-weight: font-weight('regular'),
  line-height: 130%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(5),
    ),
    lg: (
      font-size: type-scale(6),
      line-height: 125%,
    ),
    xlg: (
      font-size: type-scale(7),
      line-height: 129%,
    ),
    max: (
      font-size: type-scale(8),
      line-height: 125%,
    ),
  ),
) !default;

$expressive-heading-05: (
  font-family: font-family('sans'),
  font-size: type-scale(7),
  font-weight: font-weight('light'),
  line-height: 129%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(9),
      line-height: 122%,
    ),
    lg: (
      font-size: type-scale(10),
      line-height: 119%,
    ),
    xlg: (
      font-size: type-scale(11),
      line-height: 117%,
    ),
    max: (
      font-size: type-scale(13),
    ),
  ),
) !default;
```

```scss
// Additional styles
$quotation-01: (
  font-family: font-family('serif'),
  font-size: type-scale(5),
  font-weight: font-weight('regular'),
  line-height: 130%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(5),
    ),
    lg: (
      font-size: type-scale(6),
      line-height: 125%,
    ),
    xlg: (
      font-size: type-scale(7),
      line-height: 129%,
    ),
    max: (
      font-size: type-scale(8),
      line-height: 125%,
    ),
  ),
) !default;

$quotation-02: (
  font-family: font-family('serif'),
  font-size: type-scale(7),
  font-weight: font-weight('light'),
  line-height: 129%,
  letter-spacing: 0rem,
  breakpoints: (
    md: (
      font-size: type-scale(9),
      line-height: 122%,
    ),
    lg: (
      font-size: type-scale(10),
      line-height: 119%,
    ),
    xlg: (
      font-size: type-scale(11),
      line-height: 117%,
    ),
    max: (
      font-size: type-scale(13),
    ),
  ),
) !default;

$display-01: (
  font-family: font-family('sans'),
  font-size: type-scale(10),
  font-weight: font-weight('light'),
  line-height: 119%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(10),
    ),
    lg: (
      font-size: type-scale(12),
    ),
    xlg: (
      font-size: type-scale(13),
      line-height: 117%,
    ),
    max: (
      font-size: type-scale(15),
      line-height: 113%,
    ),
  ),
) !default;

$display-02: (
  font-family: font-family('sans'),
  font-size: type-scale(10),
  font-weight: font-weight('semibold'),
  line-height: 119%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(10),
    ),
    lg: (
      font-size: type-scale(12),
    ),
    xlg: (
      font-size: type-scale(13),
      line-height: 116%,
    ),
    max: (
      font-size: type-scale(15),
      line-height: 113%,
    ),
  ),
) !default;

$display-03: (
  font-family: font-family('sans'),
  font-size: type-scale(10),
  font-weight: font-weight('light'),
  line-height: 119%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(14),
      line-height: 115%,
    ),
    lg: (
      font-size: type-scale(17),
      line-height: 111%,
      letter-spacing: -0.64px,
    ),
    xlg: (
      font-size: type-scale(20),
      line-height: 107%,
      letter-spacing: -0.64px,
    ),
    max: (
      font-size: type-scale(23),
      line-height: 105%,
      letter-spacing: -0.96px,
    ),
  ),
) !default;

$display-04: (
  font-family: font-family('sans'),
  font-size: type-scale(10),
  font-weight: font-weight('semibold'),
  line-height: 119%,
  letter-spacing: 0,
  breakpoints: (
    md: (
      font-size: type-scale(14),
      line-height: 115%,
    ),
    lg: (
      font-size: type-scale(17),
      line-height: 111%,
      letter-spacing: -0.64px,
    ),
    xlg: (
      font-size: type-scale(20),
      line-height: 107%,
      letter-spacing: -0.64px,
    ),
    max: (
      font-size: type-scale(23),
      line-height: 105%,
      letter-spacing: -0.96px,
    ),
  ),
) !default;
```

### Global

The other categories are global and component-specific variables. These control more general styling of components, such as layer usage or border width.

```scss
// Global
$input-border: 1px solid transparent !default !global;
$input-label-weight: 400 !default !global;
$disabled: $ibm-colors__gray--30 !default !global;
$disabled-background-color: $ibm-colors__gray--10 !default !global;
$focus: $ibm-colors__blue--60 !default !global;

// Link
$link-visited: $ibm-colors__purple--60 !default !global;
$link-inverse-color: #6ea6ff !default !global;

// Tooltip
$tooltip-background-color: #3d3d3d !default !global;

// Button Theme Variables
$button-font-weight: 400 !default !global;
$button-font-size: 0.875rem !default !global;
$button-border-radius: 0 !default !global;
$button-height: 48px !default !global;
$button-padding: 0.875rem 4rem 0.875rem 1rem !default !global;
$button-padding-sm: 0.375rem 4rem 0.375rem 1rem !default !global;
$button-padding-lg: $spacing-sm !default !global;
$button-border-width: 1px !default !global;
$button-outline-width: 3px !default !global;
$button-outline-offset: -5px !default !global;
$button-outline: 1px solid $ibm-colors__white !default !global;

// Accordion (Reverse)
$accordion-flex-direction: row-reverse !default !global;
$accordion-justify-content: flex-start !default !global;
$accordion-arrow-margin: 0 $spacing-md 0 0 !default !global;
$accordion-title-margin: 0 0 0 $spacing-md !default !global;
$accordion-content-padding: 0 0 0 $spacing-md !default !global;

// Card
$card-text-align: center !default !global;
$card-flex-align: center !default !global;

// Checkbox
$checkbox-border-width: 2px !default !global;

// Code Snippet
$snippet-background-color: $ui-01 !default !global; // TODO: Define for experimental
$snippet-border-color: $ui-03 !default !global; // TODO: Define for experimental

// Content Switcher
$content-switcher-border-radius: 0px !default !global;
$content-switcher-option-border: 1px solid $brand-01 !default !global;
$content-switcher-divider: $ibm-colors__gray--30 !default !global;

// Data Table
$data-table-heading-transform: uppercase !default !global;
$data-table-heading-border-bottom: 1px solid $brand-01 !default !global;
$data-table-row-height: 2rem !default !global;

// Date Picker
$date-picker-in-range-background-color: $ibm-colors__blue--20 !default !global;

// Modal
$modal-border-top: $brand-01 4px solid !default !global;
$modal-footer-background-color: $ui-03 !default !global;

// Notification
$notification-info-background-color: $ibm-colors__blue--10 !default !global;
$notification-error-background-color: $ibm-colors__red--10 !default !global;
$notification-warning-background-color: rgba(#fdd13a, 0.15) !default !global;
$notification-success-background-color: $ibm-colors__green--10 !default !global;

// Progress Indicator
$progress-indicator-bar-width: 1px inset transparent !default !global;
$progress-indicator-stroke-width: 5 !default !global;
$progress-indicator-line-offset: 0.625rem !default !global;

//Code Snippet
$copy-active: $ibm-colors__gray--30 !default !global;
$copy-btn-feedback: $ibm-colors__gray--80 !default !global;

// Radio Button
$radio-border-width: 1px !default !global;

// Structured Theme Variables
$structured-list-padding: 2rem !default !global;
$structured-list-text-transform: none !default !global;

// Slider

//Tab
$tab-underline-color: 2px solid $ibm-colors__gray--30 !default !global;
$tab-underline-color-hover: 2px solid $ibm-colors__gray--60 !default !global;
$tab-text-disabled: $ibm-colors__gray--30 !default !global;
$tab-underline-disabled: 2px solid $ibm-colors__gray--10 !default !global;

// Toggle
$toggle-background-color: $ibm-colors__green--50 !default !global;

// Skeleton Loading
$skeleton: rgba(
  $color__blue-51,
  0.1
) !default !global; //old $field-01 TODO: Define for experimental
```

## Theming applied

The following example demonstrates the relationship between the different themes. Each theme shares the same variables and roles, with only the value changing for each individual theme.

![Default theme applied](images/themes-1.svg)

| Key | Token       | Role                | White theme value    | Dark theme value    |
| --- | ----------- | ------------------- | -------------------- | ------------------- |
| 1   | `$text-02`  | Label color         | `#565656` / Gray 70  | `#bebebe` / Gray 30 |
| 2   | `$text-01`  | Primary text color  | `#171717` / Gray 100 | `#f3f3f3` / Gray 10 |
| 3   | `$ui-04`    | Border bottom color | `#8c8c8c` / Gray 50  | `#a4a4a4` / Gray 40 |
| 4   | `$icon-01`  | Primary icon color  | `#171717` / Gray 100 | `#f3f3f3` / Gray 10 |
| 5   | `$field-01` | Field color         | `#f3f3f3` / Gray 10  | `#3d3d3d` / Gray 80 |
| 6   | `$ui-02`    | Page background     | `#ffffff` / White    | `#282828` / Gray 90 |
