# Configuração de linters

### TODO

1. [x] [ESLint](https://github.com/gabrieljmj/devio-dev-doc/blob/main/LINTERS.md#eslint-com-typescriptreact)
2. [ ] PHPCSFixer

## ESLint (com TypeScript/React)

Será usado, como base, o padrão criar pelo AirBnb, porém com modificações.

### Instalação

Instalação da configuração do AirBnb:

```console
npx install-peerdeps --dev eslint-config-airbnb
```

Instalação do restante das dependências:
```console
npm i typescript @typescript-eslint/eslint-plugin @typescript-eslint/parser prettier eslint-config-prettier eslint-plugin-prettier -D
```

### Configuração ESLint

```.eslintrc.json```
```json
{
    "extends": [
        "airbnb",
        "airbnb/hooks",
        "plugin:@typescript-eslint/recommended",
        "prettier",
        "plugin:prettier/recommended"
    ],
    "plugins": ["@typescript-eslint", "react", "prettier"],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "ecmaVersion": 2018,
        "sourceType": "module",
        "project": "./tsconfig.json"
    },
    "rules": {
        "import/no-unresolved": 0,
        "react/jsx-filename-extension": [1, {
        "extensions": [
          ".ts",
          ".tsx"
        ]
        }],
        "prettier/prettier": [
            "error",
            {
                "singleQuote": true,
                "trailingComma": "all",
                "arrowParens": "avoid",
                "endOfLine": "auto"
            }
        ],
        "no-use-before-define": "off",
        "@typescript-eslint/no-use-before-define": ["error"],
        "import/extensions": ["error", "never"],
        "react/prop-types": 0,
        "no-shadow": "off",
        "@typescript-eslint/no-shadow": ["error"],
        "react/require-default-props": 0,
        "react/jsx-props-no-spreading": 0,
        "@typescript-eslint/explicit-module-boundary-types": 0,
        "react-hooks/exhaustive-deps": 0,
        "import/prefer-default-export": 0,
        "global-require": 0,
        "camelcase": 0,
        "react/style-prop-object": 0
    }
}
```

### Extensão de VSCode

É interessante ter instalado no VSCode a
[extensão do ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) também
e habilitar essas configurações para que, ao salvar um arquivo, o ESLint já o corrija:

```json
{
    "eslint.format.enable": true,
    "eslint.packageManager": "yarn",
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "dbaeumer.vscode-eslint",
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true,
        "source.organizeImports": true
    },
    "javascript.updateImportsOnFileMove.enabled": "always",
    "eslint.alwaysShowStatus": true
}
```