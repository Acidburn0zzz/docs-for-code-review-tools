Pattern: Missing `match?` when `MatchData` is not used

Issue: -

## Description

In Ruby 2.4, `String#match?`, `Regexp#match?` and `Symbol#match?`
have been added. The methods are faster than `match`.
Because the methods avoid creating a `MatchData` object or saving
backref.
So, when `MatchData` is not used, use `match?` instead of `match`.

## Examples

```ruby
# bad
def foo
  if x =~ /re/
    do_something
  end
end

# bad
def foo
  if x.match(/re/)
    do_something
  end
end

# bad
def foo
  if /re/ === x
    do_something
  end
end

# good
def foo
  if x.match?(/re/)
    do_something
  end
end

# good
def foo
  if x =~ /re/
    do_something(Regexp.last_match)
  end
end

# good
def foo
  if x.match(/re/)
    do_something($~)
  end
end

# good
def foo
  if /re/ === x
    do_something($~)
  end
end
```

## Further Reading

* [RuboCop - Performance/RegexpMatch](https://github.com/rubocop-hq/rubocop-performance/blob/master/manual/cops_performance.md#performanceregexpmatch)
