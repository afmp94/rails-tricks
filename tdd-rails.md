## Why do TDD?

*  Business requirements  
*  Make sure it works  
*  Adding features months later  
*  Tests act as documentation  
*  Code is easier to refactor
*  Easier to modify/extend code
*  Code is written quickly by helping to guide the design decisions
*  Validates we are writing code that actually works
*  Helps developers hone in on writing code that is absolutely necessary
*  Helps establish trust among the team


**Acceptance Tests:** High level tests, driven from the user or customer of the
actual web applciation.  They would be performing high level actions.

**Unit Tests**: At a much lower level.  Given a state we need to calc the right
sales tax, etc.  Isolates small components of the application.

#### Useful Testing Tools
*  Factory Girl
*  Shoulda Matchers
*  DatabaseCleaner - ensure we have a clean slate between test runs

**TIP** run rails g to see a list of generators you have available

Stubs allow you call a method
Mocks expect you to call a method on the object


**TIP**: When using database_cleaner you will want to turn off transactional
fixtures

```ruby
# DB cleaner configuration from Avdi Grimm
RSpec.configure do |config|

  config.before(:suite) do
    DatabaseCleaner.clean_with(:truncation)
  end

  config.before(:each) do
    DatabaseCleaner.strategy = :transaction
  end

  config.before(:each, :js => true) do
    DatabaseCleaner.strategy = :truncation
  end

  config.before(:each) do
    DatabaseCleaner.start
  end

  config.after(:each) do
    DatabaseCleaner.clean
  end

end
```

Transactional fixtures true will clear the entire test database after the test is
run, however sometimes there are errors where models will get persisted when you
don't want it to.



