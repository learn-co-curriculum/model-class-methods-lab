# Optimal Queries using Active Record

## Learning Goals

* Use ActiveRecord's AREL library to build optimized queries

## Introduction

In programming, a good maxim is this:

> Use the best tool for the job

For example, you don't want to use JavaScript to build a computer for flying to
the Moon. JavaScript doesn't have very good decimal precision and, at distances
as far as the Moon, getting a number off in the hundred-thousandths place after
the decimal is the difference between landing on that celestial orb or taking a
long trip through nothing, forever.

Databases are AMAZING at linking and summarizing data. Ruby is a nice
general-purpose programming language. So when we need to get data from a
database, we want to ask the DATABASE to do as much of that work as possible.
That's what it's good at. That's what it likes to do. It has sacrificed some
capabilities in order to do other capabilities ***extremely well***.

If you use this code:

```ruby
doctors = Doctor.all
first_six_drs = doctors[0..5]
```

You will get six doctors by using _RUBY_ to "section off" six doctors using
Ruby's range method (`[]`). But under the covers we asked the database for
**all** the doctors and then took six of them. Wouldn't it make more sense to
ask the database to get us ***only*** six `Doctor`s in the first place? That's
what the following code does:

```ruby
Doctor.limit(6).to_a
```

ActiveRecord has a number of "finder" methods like `limit` built right in. These
methods let us query the database, via ActiveRecord, in an
object-oriented-looking way that uses as much of the database's power as
possible.

## Use ActiveRecord's Finder Methods To Build Optimized Queries

In this lab, we've provided the solution (commented out) to the tests. You
should step through the tests and "fix" each method to make the test pass.

As you uncomment, be sure to evaluate the implementation we've provided you.
Methods like `order`, `where`, `includes` are all ActiveRecord finder methods.
You should look up these methods in the [ActiveRecord Query Interface
documentation][query-interface], and see how they're working to filter the data
retrieved from the database before the result "gets to Ruby-land."

## Conclusion

While it's not necessary to memorize all the chainable methods
ActiveRecord provides, it's best to know some of the common methods you saw in this
lab. If you are working in a Rails environment, finder methods can make your queries
more efficient, which can literally speed up your applications 1000x!

[query-interface]: https://guides.rubyonrails.org/active_record_querying.html
