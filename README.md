## Design Tokens

### Given the list of design tokens provided, describe how you would reconfigure these tokens to be efficiently consumed by a ReactJS web application. What format would you recommend these tokens be in? Explain your reasoning.

Design tokens are vital for storing all the design decisions used within the design system. 
These decisions cover a variety of elements that define the product and brand, like colors, typography, borders, animations, and measurements. 

The tokens provided in the JSON file look like primitive tokens, which are the most basic form of tokens. The goal of Primitive Tokens is to create a robust palette that resonates with the brand identity.

Ideally, I would use a combination of primitives and semantic tokens. Semantic tokens carry meaning and imply how and where they should be applied. They typically reference only the primitive tokens but include guidance on how colors should be used in text, the types of text to use, etc., embedding both meaning and guidance within.

Design tokens connect style choices that would otherwise lack a clear relationship.

Given this,  I would split the tokens into categories:

```javascript
{
    colors: {
        primary: {
            light: '#007BFF',
            dark: "#BB86FC"
        },
        secondary: {
            light: "#6C757D",
            dark: "#03DAC6",
        },
        accent: {
            light: "#28A745"
            dark: "#CF6679"
        },
        error: {
            light: "#DC3545",
            dark: "#CF6679"
        },
        info: {
            light: "#17A2B8",
            dark: "#03A9F4",
        },
        success: {
            light: "#28A745",
            dark: "#81C784",
        },
        text: {
            light: "#333333",
            dark: "#E0E0E0",
        },
        background: {
            light: "#FFFFFF",
            dark: "#121212",
        }
    },
    typography: {
        fontFamily: "'Helvetica Neue', Arial, sans-serif",
        fontSize: "16px",
        fontWeightNormal: "400",
        fontWeightBold: "700",
    },
    spacing: {
        small: "8px",
        medium: "16px",
        large: "24px",
    },
    border: {
        radius: {
            small: "4px",
            medium: "8px",
            large: "12px"
        }
    }
}
```

### How would you implement a light and dark theme in the application using these design tokens? Describe your approach in detail.

For light and dark themes, there's usually some shared values.
For the shared values, I would create a `core` object. The would include values like `white`, brand colors.

The colors should be optimized to be consistent across both modes, and they should meet the acessibility criteria.

With this in mind, we'd have to define the variants for `dark` and `light` modes.
```javascript
{
    core: {
        white: "value",
        brand: "value",
    },
    dark: {
        primary: {
            light: "value",
            dark: "value"
        }
    },
    light: {
        primary: {
            light: "value",
            dark: "value"
        }
    }
}
```