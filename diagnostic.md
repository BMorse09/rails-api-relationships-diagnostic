# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

```sh
  Join tables are valuable because they allow you to combine two tables and
  return a new set of data while preserving the original state of the data
  that you\'re combining.
```

1.  Provide a database table structure and explain the Entity Relationship that
describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
(Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
`Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
join table with references to `Movies` and `Profiles`.

```sh
Profiles
 - given_name | text
 - surname | text
 - email | text

Movies
 - title | text
 - release_date | date
 - length | integer

 Favorites
 - profiles_id | integer
 - movies_id | integer
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Profile < ActiveRecord::Base
A Profile has many Movies through Favorites
end
```

```rb
class Movie < ActiveRecord::Base
A Movie has many Profiles through Favorites
end
```

```rb
class Favorite < ActiveRecord::Base
Favorites have many Movies through Profiles
end
```

1.  What is the purpose of a serializer? What would our `Profile` serializer look
like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

```sh
The serializer represents each resource that it inherits as a class, thus allowing
us a way of creating custom JSON.

```

```rb
class ProfileSerializer < ActiveModel::Serializer
profiles: [
      {
        id: 1
        given_name: Benjamin
        surname: Morse
        email: benmorse09@gmail.com

      }

]
end
```

1.  What would the command be to _scaffold_ out a **join table** for Favorites from
the above `Movies` and `Profiles`.

```sh
  rails g migration create_Favorites Profiles_id:integer Movies_id:integer
```

1.  What is `Dependent: Destroy` and where/why would we use it?

```sh
Dependent: Destroy will destroy all objects associated with their owner. We
would use it when we want to destory all the objects associated with an owner?

```

1.  Think of **ANY** example where you would have a one-to-many relationship as well
as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

```sh
  # < Your Response Here >
```
