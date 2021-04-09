# Getting started

```shell
yarn add --dev eslint prettier eslint-plugin-react eslint-plugin-react-hooks eslint-config-prettier eslint-plugin-prettier eslint-plugin-jsx-a11y
```
## .eslintrc.js .prettierrc
```shell
touch .eslintrc.js .prettierrc
```

## .eslintignore and .prettierignore
```shell
touch .eslintignore .prettierignore
```
Just add the follwing to both files
```shell
node_modules
```

## .prettierrc
```shell
{
    "semi": true,
    "tabWidth": 4,
    "printWidth": 100,
    "singleQuote": true,
    "trailingComma": "none",
    "jsxBracketSameLine": true
}
```

## .eslintrc.js
```js
module.exports = {
    root: true,                 // Make sure eslint picks up the config at the root of the directory
    parserOptions: {
        ecmaVersion: 2020,      // Use the latest ecmascript standard
        sourceType: 'module',   // Allows using import/export statements
        ecmaFeatures: {
            jsx: true           // Enable JSX since we're using React
        }
    },
    settings: {
        react: {
            version: 'detect'   // Automatically detect the react version
        }
    },
    env: {
        browser: true,          // Enables browser globals like window and document
        amd: true,              // Enables require() and define() as global variables as per the amd spec.
        node: true              // Enables Node.js global variables and Node.js scoping.
    },
    extends: [
        'eslint:recommended',
        'plugin:react/recommended',
        'plugin:jsx-a11y/recommended',
        'plugin:prettier/recommended' // Make this the last element so prettier config overrides other formatting rules
    ],
    rules: {
        'prettier/prettier': ['error', {}, { usePrettierrc: true }]  // Use our .prettierrc file as source
    }
};
```

## Running ESlint
You need to add the script to your `package.json` file.
```json
  "scripts": {
    "lint": "eslint --fix .",
    "format": "prettier --write './**/*.{js,jsx,ts,tsx,css,md,json}' --config ./.prettierrc"
  },
```

# Targeting Next.js
## .eslint.js 에 규칙추가 
```shell
{
    rules: {
        'react/react-in-jsx-scope': 'off',
        'jsx-a11y/anchor-is-valid': [
            'error',
            {
                components: ['Link'],
                specialLink: ['hrefLeft', 'hrefRight'],
                aspects: ['invalidHref', 'preferButton']
            }
        ]
    }
}
```