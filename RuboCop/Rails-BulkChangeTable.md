Pattern: Missing use of `change_table` with `bulk: true`

Issue: -

## Description

This rule checks whether alter queries are combinable.
If combinable queries are detected, it suggests to you
to use `change_table` with `bulk: true` instead.
When use this method, make combinable alter queries
a bulk alter query.

The `bulk` option is only supported on the MySQL and
the PostgreSQL (5.2 later) adapter; thus it will
automatically detect an adapter from `development` environment
in `config/database.yml` when the `Database` option is not set.
If the adapter is not `mysql2` or `postgresql`,
this rule ignores offenses.

## Examples

```ruby
# bad
def change
  add_column :users, :name, :string, null: false
  add_column :users, :nickname, :string

  # ALTER TABLE `users` ADD `name` varchar(255) NOT NULL
  # ALTER TABLE `users` ADD `nickname` varchar(255)
end

# good
def change
  change_table :users, bulk: true do |t|
    t.string :name, null: false
    t.string :nickname
  end

  # ALTER TABLE `users` ADD `name` varchar(255) NOT NULL,
  #                     ADD `nickname` varchar(255)
end
```
```ruby
# bad
def change
  change_table :users do |t|
    t.string :name, null: false
    t.string :nickname
  end
end

# good
def change
  change_table :users, bulk: true do |t|
    t.string :name, null: false
    t.string :nickname
  end
end

# good
# When you don't want to combine alter queries.
def change
  change_table :users, bulk: false do |t|
    t.string :name, null: false
    t.string :nickname
  end
end
```

## Default configuration

Attribute | Value
--- | ---
Database | `<none>`
Include | `db/migrate/*.rb`

## Further Reading

* [RuboCop - Rails/BulkChangeTable](https://github.com/rubocop-hq/rubocop-rails/tree/master/lib/rubocop/cop/rails#railsbulkchangetable)
