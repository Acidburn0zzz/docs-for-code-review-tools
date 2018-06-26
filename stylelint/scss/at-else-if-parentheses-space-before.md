Pattern: Malformed space before `@else if` parentheses

Issue: -

## Description

Require or disallow a space before `@else if` parentheses.

```scss
@else if ($condition) { }
/**      ↑
 * The space before this parenthesis */
```

## Examples

`string`: `"always"|"never"`

### `"always"`

There *must always* be exactly one space between the `@else if` and the condition opening parenthesis. 

*Note: This rule does not enforce parentheses to be present.*

The following patterns are considered warnings:

```scss
@else if($condition) { }
```
```scss
@else if  ($condition) { }
```

The following patterns are *not* considered warnings:

```scss
@else if ($condition) { }
```
```scss
@else if $condition { }
```

### `"never"`

There *must never* be whitespace between the `@else if` and the condition opening parenthesis. 

The following patterns are considered warnings:

```scss
@else if ($condition) { }
```

The following patterns are *not* considered warnings:

```scss
@else if($condition) { }
```
```scss
@else if $condition { }
```

## Further Reading

* [stylelint-scss - at-else-if-parentheses-space-before](https://github.com/kristerkari/stylelint-scss/blob/master/src/rules/at-else-if-parentheses-space-before)