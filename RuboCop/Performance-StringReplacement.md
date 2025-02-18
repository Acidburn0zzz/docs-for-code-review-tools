Pattern: Use of `gsub` instead of `tr`/`delete`

Issue: -

## Description

This rule identifies places where `gsub` can be replaced by `tr` or `delete`.

## Examples

```ruby
# bad
'abc'.gsub('b', 'd')
'abc'.gsub('a', '')
'abc'.gsub(/a/, 'd')
'abc'.gsub!('a', 'd')

# good
'abc'.gsub(/.*/, 'a')
'abc'.gsub(/a+/, 'd')
'abc'.tr('b', 'd')
'a b c'.delete(' ')
```

## Further Reading

* [RuboCop - Performance/StringReplacement](https://github.com/rubocop-hq/rubocop-performance/blob/master/manual/cops_performance.md#performancestringreplacement)
* [https://github.com/JuanitoFatas/fast-ruby#stringgsub-vs-stringtr-code](https://github.com/JuanitoFatas/fast-ruby#stringgsub-vs-stringtr-code)
