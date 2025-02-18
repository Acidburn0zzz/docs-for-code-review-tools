Pattern: `only`/`except` options not explicitly defined 

Issue: -

## Description

This rule checks that methods specified in the filter's `only` or `except` options are explicitly defined in the class or module.

You can specify methods of superclass or methods added by mixins on the filter, but these confuse developers. If you specify methods where are defined on another classes or modules, you should define the filter in that class or module.

## Examples

```ruby
# bad
class LoginController < ApplicationController
  before_action :require_login, only: %i[index settings logout]

  def index
  end
end

# good
class LoginController < ApplicationController
  before_action :require_login, only: %i[index settings logout]

  def index
  end

  def settings
  end

  def logout
  end
end
```
```ruby
# bad
module FooMixin
  extend ActiveSupport::Concern

  included do
    before_action proc { authenticate }, only: :foo
  end
end

# good
module FooMixin
  extend ActiveSupport::Concern

  included do
    before_action proc { authenticate }, only: :foo
  end

  def foo
    # something
  end
end
```

## Default configuration

Attribute | Value
--- | ---
Include | `app/controllers/**/*.rb`

## Further Reading

* [RuboCop - Rails/LexicallyScopedActionFilter](https://github.com/rubocop-hq/rubocop-rails/tree/master/lib/rubocop/cop/rails#railslexicallyscopedactionfilter)
* [https://github.com/bbatsov/rails-style-guide#lexically-scoped-action-filter](https://github.com/bbatsov/rails-style-guide#lexically-scoped-action-filter)
