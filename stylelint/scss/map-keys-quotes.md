Pattern: Unquoted map key

Issue: -

## Description

Require quoted keys in Sass maps.

```scss
$test: (Helvetica: 14px, Arial: 25px);
  /**   ↑                ↑
   * These words should be quoted.
   */
```

## Examples

### `always`

The following patterns are considered violations:

```scss
$test: (Helvetica: 14px, Arial: 25px);
```

The following patterns are _not_ considered violations:

```scss
$test: ("foo": 14px, "bar": 25px);
```

## Further Reading

* [stylelint - map-keys-quotes](https://stylelint.io/user-guide/rules/map-keys-quotes)