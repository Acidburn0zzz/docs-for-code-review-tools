Pattern: Missing `!default` flag for `$`-variable

Issue: -

## Description

Require `!default` flag for `$`-variable declarations

```scss
$variable: 10px !default;
/**             ↑
 * This is variable with default value */
```

## Optional Options

### `ignore: "local"`

Makes this rule ignore local variables (variables defined inside a rule/mixin/function, etc.).

The following patterns are *not* considered warnings:

```scss
$var: 10px !default;

a {
  $local-var: 10px;
}
```

## Further Reading

* [stylelint-scss - dollar-variable-default](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/dollar-variable-default/README.md)