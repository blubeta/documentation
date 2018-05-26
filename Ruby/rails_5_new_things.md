## Rails 5 differences to be aware of!

*  `belongs_to` association required by default.

- I had to add 
```class Ticket < ApplicationRecord
  belongs_to :user, optional: true
end
```
in order to create a standalone ticket that persisted to the database.