````{margin}
```{admonition} User types
:class: tip
This section is useful for user type 3-5.
```
+++
{bdg-primary}`Sphinx Extension`
````

```{include} README.md
```

## Configuration

The extension provides several configuration values, which can be added to `_config.yml`:

```yaml
sphinx: 
    config:
        sphinx_codex_name:                 ""    # default value
        sphinx_codex_style_from_proof:     true  # default value
        sphinx_codex_icon_from_proof:      false # default value
        sphinx_codex_merge_with_proof:     false # default value
```

- `sphinx_codex_name`: `""` (_default_) or `string`:
  - if `""` all `codex` directives will have the title "Code example" and will be referred to as "Code example" in the text.
  - if a `string` is provided, all `codex` directives will have the title set to that string and will be referred to as that string in the text.
- `sphinx_codex_style_from_proof`: `true` (_default_) or `false`:
  - if `true`, the CSS color style of the `codex` directive will be taken from the `prf:example` directive from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension.
  - if `false`, the CSS color style of the `codex` directive will be taken from the general `admonition` directive.
- `sphinx_codex_icon_from_proof`: `true` (_default_) or `false`:
  - if `true`, the icon of the `codex` directive will be taken from the `prf:example` directive from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension.
  - if `false`, the icon of the `codex` directive will be set to <i class="fa-solid fa-code"></i>.
- `sphinx_codex_merge_with_proof`: `false` (_default_) or `true`:
  - if `true`, the `codex` directive will be merged with the `prf:example` directive from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension. This means that:
    - All `codex` directives and `prf:example` directives will be named "Example" (unless set otherwise) and styled (color and icon) as defined by the `prf:example` directive from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension.
    - The numbering of the `codex` directives will be merged with the numbering of the `prf:example` directives from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension.
  - if `false`, the `codex` directive will not be merged with the `prf:example` directive from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension. This means that:
    - All `codex` directives will be named "Code example" (unless set otherwise) and styled (color and icon) as defined by the `sphinx_codex_style_from_proof` and `sphinx_codex_icon_from_proof` configuration values.
    - The numbering of the `codex` directives will be independent of the numbering of the `prf:example` directives from the [sphinx-proof](https://github.com/executablebooks/sphinx-proof) extension.

## Usage

This extension provides three directives:

- `codex`
- `codex-start`
- `codex-end`

### `codex` directive

```{warning}
Although this directive is called `codex`, it does not imply that the code is executable. It is simply a directive to create the possibility to use one extension for both executable and non-executable (code) examples.
```

The `codex` directive is used to create a code example with runnable code. It can be used as with the following minimal syntax:

````md
:::{codex}
:label: my-example

Content of the directive.
:::
````

This will be rendered as

:::{codex}
:label: my-example

Content of the directive.
:::

### `codex-start` and `codex-end` directives

The `codex-start` and `codex-end` directives are used to create a code example with runnable code. They can be used as follows:

````md
:::{codex-start}
:label: my-rendered-example

Initial content of the directive.
:::

Other content of the directive, such as code blocks or text, can be added here.

For runnable code, include the code as you are used to outside any other directive.

:::{codex-end}
:::
````

This will be rendered as

:::{codex-start}
:label: my-rendered-example

Initial content of the directive.
:::

Other content of the directive, such as code blocks or text, can be added here.

For runnable code, include the code as you are used to outside any other directive:

:::{codex-end}
:::