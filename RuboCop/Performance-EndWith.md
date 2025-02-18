Pattern: Missing use of `String#end_with?`

Issue: -

## Description

This rule identifies unnecessary use of a regex where `String#end_with?` would suffice.

## Examples

```ruby
# bad
'abc' =~ /bc\Z/
'abc'.match(/bc\Z/)

# good
'abc'.end_with?('bc')
```

## Further Reading

* [RuboCop - Performance/EndWith](https://github.com/rubocop-hq/rubocop-performance/blob/master/manual/cops_performance.md#performanceendwith)
* [https://github.com/JuanitoFatas/fast-ruby#stringmatch-vs-stringstart_withstringend_with-code-start-code-end](https://github.com/JuanitoFatas/fast-ruby#stringmatch-vs-stringstart_withstringend_with-code-start-code-end)
