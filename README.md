# Quiz #3

## Instructions

1. Fork this repo
2. Clone your fork
3. Fill in your answers by writing in the appropriate area, or placing an 'x' in
the square brackets (for multiple-choice questions).
4. Add/Commit/Push your changes to Github.
5. Open a pull request.

**Note**: only place your answer between backticks. Don't modify the backticks,
or the language specifier after them.

## Ruby Basics & Enumerables (meets Beauty and the Beast)


### Question 1

Define a method called `offerRose`, which should take one argument named person.

When called, the method should `puts`, "Would you take this rose and help out
an old beggar, X?", where X is the person passed into the method.

Demonstrate calling the method with an argument of "young prince".

Write your code here:
```ruby
def offerRose( person )
  puts "Would you take this rose and help out an old beggar, #{person}?"
end

offerRose( "young prince" )
```

### Question 2

Assume the following hash:

```ruby
town = {
  residents: ["Maurice", "Belle", "Gaston"],
  castle: {
    num_rooms: 47,
    residents: "Robby Benson",
    guests: []
  }
}
```

Using Ruby, remove Belle from the town residents, and
add her to the list of guests in the castle.

Write your code here:
```ruby
town[:residents].delete( "Belle" )
town[:castle][:guests] = "Belle"
```

### Question 3

Assume you have an array of strings representing friend's names:

```ruby
friends = ["Chip Potts", "Cogsworth", "Lumière", "Mrs. Potts"]
```

Using `.each` AND string interpolation, produce output (using `puts`) like so:

```
Belle is friends with Chip Potts
Belle is friends with Cogsworth
Belle is friends with Lumière
Belle is friends with Mrs. Potts
```

Write your code here:
```ruby
friends.each { |name|
    print "Belle is friends with #{name}"
}
```

## SQL, Databases, and ActiveRecord (meets Aladdin)

### Question 4

Describe what an ERD is, and why we create them for applications. Also give an
example what the attributes and relationships might be for the following
entities (no need to draw an ERD):
<!-- Maybe clarify whether they're meant to give relationships between all four entities or... -->
* Genie
* Lamp
* Person
* Pet

Your answer:
```
An Entity Relationship Diagram is used to visualize and plan the ways different sets of information in the database, typically tables, interact before you begin developing the app.

For the examples given. A Gene has a one-to-one relationship with a lamp. A person can have a one to many relationship with a lamp or genie, if they're especially lucky. A person may have a one-to-many relationship to pets, as they could have multiple. Or in the case of a family with multiple pets, it would be a many-to-many relationship.
```

### Question 5

Describe what a schema is, and how we represent a one-to-many relationship in a
SQL database. If you need an example, you can use: people and wishes
(one-to-many).

Your answer:
```
A schema details the basic structure of the tables in the database. Essentially, it describes each table's columns and what their data type is as well as sets the relationships the tables have with eachother.

A one-to-many relationship would be shown using "belongs_to" and "has_many".
```

### Question 6

**Assume:**
1. Your database has two working tables, `genies` and `lamps`.
2. You have a working connection to the database for ActiveRecord.
3. You have active record models defined for `Genie` and `Lamp`, and the
relationships between the two are set up in Active Record.
<!-- Do we want to specifiy what kind of relationship they have, in case some students aren't familiar with the mythology...? -->
4. Lamps have one property, `wishes_remaining`, and genies have one property, `name`.

Write code to do the following:

1. Create a lamp with 3 wishes remaining and a genie named 'Genie'
2. Create a relationship between 'Genie' and the lamp.
3. Update the lamp so it only has one wish left.
  * Oh no... Jafar has Aladdin! Thankfully he's wished to become a genie himself!
4. Create a new Genie named 'Jafar' and put him in a new lamp with 3 wishes left.
5. Free the good Genie by setting his lamp to `nil`


Write your code here:
```ruby
# I'm not sure what I need to do here. Will study up on this asap.
```

## Sinatra / REST (meets Mulan)

### Question 7

The Chinese Emperor needs an application to help him manage his warriors.
<!-- LOLZ. YES. -->

Describe to him what a RESTful route is, and list what the seven RESTful routes would look like for such an application.

Your description:
```
A RESTful route is one of seven actions you can take to create, edit, show, or delete information in the database.
```
Your routes:
```
The ancestors have provided an example of one route; you do the other six!

GET '/warriors'
  * This is the index route that displays all the warriors the emperor has in his army

GET '/warriors/new'
  * This is the new route that renders a form to add a new warrior to his army.

POST '/warriors'
  * This is the create route that posts the information placed in the "new" route form.

GET '/warriors/:id'
  * This is the show route, which finds a warrior by ID, and displays information about that warrior.

GET 'warriors/:id/edit'
  * This is the edit route that allows the emperor to make changes to the an individual warrior's page using a form rendered in the browser.

PUT 'warriors/:id'
  * This is the update route that takes the information from the edit route and makes the changes in the database

DELETE 'products/:id'
  * This is the delete route that deletes the warrior from the database.
```

### Question 8

Assume:
* Warrior is an ActiveRecord model, with a 'name' attribute.
* You have a Sinatra `app.rb` (or similar file), that defines the following
route:

```ruby
get '/warriors' do
  @warriors = Warrior.all
  erb :"warriors/index"
end
```

Write what an example ERB file (aka view) might look like to list all the warriors:

Write your code here (**NOTE: syntax highlighting doesn't work for ERB in markdown files, so ignore the colors!**):
```html
<body>
  <section id="warriors">
    <p><% @warriors.each do |warrior| %>
      <p><%= warrior.name %></p>
    <% end %>
  </section>
</body>
```
