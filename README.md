## Design Tokens

### Given the list of design tokens provided, describe how you would reconfigure these tokens to be efficiently consumed by a ReactJS web application. What format would you recommend these tokens be in? Explain your reasoning.

Design tokens point to style values, like colors, fonts, and measurements. Usually, each token is named for how and where it's used.

Design tokens connect style choices that would otherwise lack a clear relationship.

Because tokens enable a design system to have a single source of truth, and because they are reusable and purpose-driven, and they can define systems and contexts for use, I would split the tokens into categories:

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
            ligth: "#DC3545",
            dark: "#CF6679"
        },
        info: {
            light: "#17A2B8",
            dark: "#03A9F4",
        },
        success: {
            ligth: "#28A745",
            dark: "#81C784",
        },
        text: {
            ligth: "#333333",
            dark: "#E0E0E0",
        },
        background: {
            ligth: "#FFFFFF",
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
