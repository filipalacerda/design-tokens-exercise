## Design Tokens

### Given the list of design tokens provided, describe how you would reconfigure these tokens to be efficiently consumed by a ReactJS web application. What format would you recommend these tokens be in? Explain your reasoning.

Design tokens are vital for storing all the design decisions used within the design system. 
These decisions cover a variety of elements that define the product and brand, like colors, typography, borders, animations, shadows, opacity, and measurements. 

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
For the shared values, I would create a `global` theme. This would be the foundations theme. That would include values like `white`, brand colors.

The colors should be optimized to be consistent across both modes, and they should meet the acessibility criteria.

Then, I would create a light and a dark theme, with different tokens sets.
With this in mind, we'd have to define the primitives variants for `dark` and `light` modes.
```javascript
{
    global: {
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

### Are there any tools or processes you would introduce to manage design tokens and aid in the implementation of the light and dark themes? Describe how these tools would integrate with the current workflow.

There are a few tools and processes that can make the implementation of design tokens easier.

[Tokens Studio](https://tokens.studio/), a Figma plugin, allows the team to create, edit, and manage tokens and integrate them with code.

It's also possible to use variables in Figma that sync with the existing design tokens with the Tokens Studio plugin, but I believe this is a beta feature.

Code-wise, we'd have the design tokens in a JSON format. We would then have a transformer, like [Style Dictionary](https://amzn.github.io/style-dictionary/#/) that would generate outputs like CSS and synchronize with Figma variables. This way, we would have a single source of truth, that would work across different platforms and applications.

### If possible provide examples from your experience where you have implemented similar strategies where appropriate

I had two experiences with Design Systems in the past:

1. At Zapier, I was on the Design Systems team for about 8 months. Our main focus was more on the JavaScript side than on defining tokens. - This job was already done when I joined.
At Zapier, we had no dark and light mode to handle.

With this team, I was focused on creating and maintaining reusable components.
We owned a npm package with all the components that the entire company would use - around 2000 people. The teams using them were very different, from Marketing to Frontend Engineers.

We worked together with Designers to ensure we were implementing the correct design for each component, keeping in mind accessibility, unit tests, end-to-end tests, and responsive designs.
The design specs were delivered to us through Figma and we would implement React components using emotion CSS for styling the components.

While on this team, I lead the migration from Styleguidist to Storybook. This enabled us to have accessibility checks for each component.

2. At Lively, I've worked together with the principal designer to ensure the code and the figma tokens were synchronized:
    1. When I joined the team, the primitives being used in the tokens were outdated with the new Figma tokens.
    1. I worked together with the Principal Designer, to name each primitive. This involved understanding where in the code each color would be used (if it was text/background/border), how many times a primitive was being used, or if it was used in different contexts.
    1. After creating the name convention, and because we were using Material UI, I extended the `palette` option to contain both MaterialUI's main primitives and our custom primitives.
    1. The next step of the work was to update every reusable component, and every other component to use the new primitives instead of the old ones.
    1. After this work was completed, we did the same for the Typography primitives.
I've also worked in two other aspects of the design system within this company: unit tests and accessibility.
None of the reusable components had unit tests, they would only have some documentation on Storybook. I added unit tests for all of the reusable components.
Regarding accessibility, my work focused on two key factors: 
   1. Enabling the accessibility checks on Storybook - there were a lot of failures, from color contrast to bad nested heading levels. I fixed all of the errors, by working together with the Design team regarding adjusting the colors to fix the color contrast errors.
   1. Enabling unit tests for accessibility. I used a tool called [jest-axe](https://www.npmjs.com/package/jest-axe). This tool does not guarantee that the code is 100% accessible, but it does perform some checks. However, together with the Storybook accessibility add-on, we'd have full coverage. I added this step to the GitHub Actions Pipeline to prevent new code from being added that would not meet a11y checks and I fixed all the a11y errors.

3. Before working at these two companies, I was invited to write a few blog posts about reusable components. At the time I was working with Vuejs, so the articles are about how to write them with Vuejs. You can find them listed [here](https://www.filipalacerda.com/resources#posts):
    1. [How To Build a Modal Component with Vue.js](https://www.digitalocean.com/community/tutorials/vuejs-vue-modal-component)
    1. [How To Build an Autocomplete Component with Vue.js](https://www.digitalocean.com/community/tutorials/vuejs-vue-autocomplete-component)
    1. [How to Create an Accessible Autocomplete Component with Vue.js](https://www.digitalocean.com/community/tutorials/vuejs-vue-a11y-autocomplete)
    1. [How To Build a Reusable Pagination Component with Vue.js](https://www.digitalocean.com/community/tutorials/vuejs-vue-pagination-component)
