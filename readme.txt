Objective 1: Defining Test Scenarios
Let’s imagine you are assigned to test www.saucedemo.com. Your goal is to test logging
into the application with a standard user, adding to cart the Sauce Labs Fleece Jacket,
and validating the cart as the expected item.
● https://www.saucedemo.com/
● standard_user (password is on site)
● Add Fleece Jacket to shopping cart
● Validate cart contains fleece jacket

Objective 2: Defining Test Data
In the problem above, how would you define test data against which you could run your
scenarios? What about other users or selecting a different item? What’s your approach?

In this case, the scenario definition above does not have enough data.  The scenario requires
at a very minimum the following data which can be found in the application:

- Exact username
- Exact password
- Exact product name(s)

If we need to test multiple users and products, those are just data variations.  The approach
for dealing with the variations is to make an object that has those properties.  The data
source could be JSON, XML, DB, etc.  The data would be read in based in the test being run
and it would execute using the object's properties.  This avoids having any test data hard
coded and allows easy maintenance of the data. Using that data object you can test scenarios

Login:
- User login and locked out error
- User login and has a performance issue with the login service
- User login happens correctly
- User login with unknown and unknown error

Test:
- Add invalid item

Workflows:
- Add 1 valid item
- Add 0 items
- Add 1+ valid items

It's possible to test other scenarios by adding more to the JSON and Java POJO.  Allows
testing without having to change the data interface very much.

Objective 3: Test Automation
Based on your scenario(s) above and test data approach, create some executable
test(s). You can use any language you are comfortable with selenium or any other web
driver. The test(s) should be organized using POM (page object model).
Note: We are not looking for a comprehensive solution. The following are skills that we
access:

1. Ability to understand a feature and break it down
2. Ability to define clear scenarios and acceptance criteria
3. Experience with setting up test data and resolving dependencies on external services
4. Basic programming skills
5. Understanding of the page object model
6. Expertise automating tests for javascript/HTML based applications
7. Working knowledge of selenium or other web driver
8. Passion for creating simple, effective and working solutions

The test steps for the workflow
1) Login using a user
2) Verify you are on the Products page
3) Verify items wanting to be added to the cart exist in the Products page
4) Add all products
5) Go to the shopping cart
6) Verify you are on the shopping cart page
7) Verify badge count is correct
8) Verify item is in cart

For a simple workflow the steps are the same.  To handle multiple products, you just
need to iterate over the products in the data and assertions.  The data values are the
only difference.  Something like this is idea for using something like TestNG's
DataProvider or some other means of iterating over it.

The other tests use the same page objects, but may do other types of assertions based
on the test needs.

To run tests

> mvn clean test