# Week 4 Assessment

### Setup
* Fork this repository
* You may make edits directly in github
* For the Exercise section, you will want to be logged in to [replit](https://replit.com)

## Questions (8 points possible)
1. In your own words, how would you define an ORM?
    * An ORM or object-relational mapping is a tool that programmers use in order to link their program to a database. This takes c# code (and other languages) and converts it into SQL behind the scenes, the ORM we use is Entity Framework.

2. Given the two classes for bike and owner, update the classes to include a one-to-many relationship where each bike has one owner, and each owner can have many bikes.

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime PurchaseDate { get; set; }
            public Owner Owner { get; set; }
        }
    }

    namespace BikeApp
    {
        public class Owner
        {
            public int Id { get; set; }
            public string Name { get; set; }
            public int Zipcode { get; set; }
            public List<Bike> Bikes { get; set; } = new List<Bike>();
        }
    }
    ```

3. When adding a new pizza table to our database, which of the following two commands would we run first? Why is it important to run these two line in that order?
    ```
    add-migration AddPizzaTable
    ```
    ```
    update-database
    ```
    * we would NEED to run add-migration first, as this is the command that creates the file that will actually create the database and its tables. update-database would do nothing if we don't already have a migration created. 

4. For all three parts of this question, imagine that you have used Entity Framework to create a database table using the following class and context. 
    * What will the table name be?
        * 'bikes'
    * What will the column name(s) be?
        * 'id' 'type' 'date' <= I would change this to be more specific, 'purchase_date'?
    * What is the name of the database you are connecting to?
        * 'bikeApp' or 'bike_app', I would name it the same as my program so that at a glance I know exactly what program it is linked to.

    ```C#
    namespace BikeApp
    {
        public class Bike
        {
            public int Id { get; set; }
            public string Type { get; set; }
            public DateTime Date { get; set; }
        }
    }

    namespace BikeApp
    {
        public class BikeContext : DbContext
        {
            public DbSet<Bike> Bikes { get; set; }
            protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) => optionsBuilder.UseNpgsql("Host=localhost;Username=postgres;Password=password123;Database=Bikes").UseSnakeCaseNamingConvention();
        }
    }
    ```

5. What type of data does the `Contains` LINQ method return?
    <br> a. String 
    <br> b. Integer 
    <br> c. Boolean
    * Contains would return a Boolean type, as the method checks if a string has the context given, if yes = true. It wouldn't make sense if contains returned anything other than True or False.

## Exercise (5 points possible)

Fork the Replit below, and complete the 5 LINQ exercises.  Add a link to your forked repl here:  * (https://replit.com/@bradenasmith/Mod2Week4Assessment-Braden-S#main.cs) *

[https://replit.com/@launch-team/Mod2Week4Assessment](https://replit.com/@launch-team/Mod2Week4Assessment?v=1)

### Submission
* Submit a link to your forked repository in the Submission form provided in your slack channel.

## Rubric

This assessment has a total of 13 points possible.  A score of **9** or higher is a pass.

As a reminder, this assessment is for students and instructors to determine if there are any areas that need additional reinforcement!
