# Food-delivery-app
Create an app using kotlin
PROBLEM STATEMENT:
Build a food ordering application with the following functionalities:
1. A ‘Welcome page’ which displays the logo and/or name of the app. Choose any name of
your choice.
2. A ‘Login Page’ which asks for users’ mobile number and password.
3. A ‘Registration Page’ which enables users to sign up for the app.
4. A ‘Forgot Password Page’ which enables users to reset their password.
5. A ‘Navigation Drawer’ with the app logo and user name on top and menu options to
open the following pages:
a. Home
b. User Profile
c. Favorite Restaurants
d. Order History
e. Frequently Asked Questions(FAQs)
f. Log out
6. The app should be able to fetch the list of all restaurant from the internet using the link
provided below:
<http://13.235.250.119/v2/restaurants/fetch_result/>
7. A ‘My Profile’ page (where the user’s name, phone number, and address is displayed).
8. A ‘Favorites’ page (where the list of all favourite restaurants is displayed).
9. An ‘Order History’ page which lists the previously placed orders of the user.
10. An ‘FAQ’ page which lists some frequently asked questions. You can create any random
questions which you feel could be relevant for a food delivery application. (Min. 5
questions)
11. A ‘Logout’ functionality which takes the user to the login page.
12. A ‘Restaurant Details’ page which displays the menu items of that particular restaurant,
each item’s price and the option to add an item to cart.
13. A ‘Cart’ which lists the items added to cart and the total amount to be paid.
We have created a sample app for you. Please refer to it for a demo. However, we encourage
you to use your own custom icons, logos, names, and colour theme. You can also change the
colour theme and design of the application.
Click here to download demo app
SPECIFICATIONS:
Welcome Page
This will be the first page which gets displayed when the user opens the app. This page will
contain the app name and/or app logo. You can also use any custom background for this page.
This page will be displayed for 1 second and then it moves on to the login page* without any
user interaction.
(*If the user has previously logged into the application, then the next page should be ‘All
Restaurants’ page else the next page should be login page only).
Login Page
The login page is displayed after the welcome page. The user should be able to enter the
mobile number and password to login into the app. It should perform validations which checks
for the length of mobile number (should be 10), length of the password (should be more than
4) and also authenticates the login with the API given below:
<http://13.235.250.119/v2/login/fetch_result/>
If the login is successful then the app is redirected to home page otherwise it should show the
corresponding error. The login page should also have an option for users to register for the
application if they are not already registered.
Registration Page
The page should contain the following fields namely: Name, Email Address, Mobile Number,
Delivery Address, and Password which users will input and register for the app. The
registration process will send the details to the server using the link:
<http://13.235.250.119/v2/register/fetch_result>
If the registration process is successful the app should take the user to the home page which is
the page listing all the restaurants.
Forgot Password Page
The page is used to reset the user password. This will be a two-step process.
Step 1:
The information asked from the user will be the Registered Mobile Number which will be used
to verify the user mobile number and the registered email address. Then you need to send the
OTP via email using the below API:
<http://13.235.250.119/v2/forgot _password/fetch_result>
Please note that you just need to send the mobile number to the server and the process of
sending the email will be taken care of by the API itself.
Step 2:
Now once the user receives the OTP, on the next page we will ask him to enter the OTP and the
new password, which will be sent to the server along with the registered mobile number (which
is carried forward using the Bundle to this page) at the API given below which will reset the
password to its new value. The user will now be redirected to the login page where he can use
the new password to login into the application.
<http://13.235.250.119/v2/reset_password/fetch_result>
(The OTP email would be sent only once in 24 hours. Hence, if you need to reset the password
multiple times within 24 hours kindly use the same OTP)
Navigation Drawer
The navigation drawer is needed so that the user can navigate to different pages inside the app.
The user should be able to access the navigation drawer on all the app screens by clicking the
hamburger button on the left side of the toolbar or by swiping right from the left edge. It will
have a header section at the top which contains the app logo and below it should be the name
of the user. Below the header section, there will be options for ‘Home’, ‘My Profile’, ‘Favorite
Restaurants’, ‘Order History’, ‘FAQ’, and ‘Logout’ in a list style. Clicking on any option will open
the corresponding screen or perform the corresponding action.
All Restaurants Page
The ‘All Restaurants’ page will be the homepage of the app, meaning when the app is launched
and the user has already once logged into the app then the user will see the ‘All Restaurants’
page screen after the splash screen. Once the app is launched, all the restaurants will be
fetched from the server using the given link:
<http://13.235.250.119/v2/restaurants/fetch_result/>
and will be displayed on the ‘All Restaurants’ page in the form of a list. For each restaurant on
the list, the user should see the name of the restaurant, its rating, and the cost for one person.
If there is an error then suitable error handling should be done. When the user clicks on any
restaurant, the ‘Restaurant details’ page should open.
- On the homepage, the toolbar should have menu options using which the user should
be able to sort the restaurant list according to cost (low to high), cost (high to low),
rating, and cost for one.
Restaurant Details Page
The restaurant details are used to display the menu of the restaurant. When clicked on any
restaurant we send a request to the server using the link:
<http://13.235.250.119/v2/restaurants/fetch_result/id>.
We display the result of menu items in the form of a list. Each item will have a button alongside,
which will be used to add or remove that particular item from the cart. Any item should be
added to the cart only once. Here you need to finalise your order.
- Pressing back from this page should clear the items added in the cart.
- The proceed to cart button should be hidden when there are no items in the cart and
should automatically appear when we add items to cart.
- Clicking the proceed to cart button should take the user to the cart page.
 
Cart Page
The cart page contains all the items added to the cart along with their individual prices. A total
cost of all the items should be displayed on the page. These details should be fetched from the
local database where you will save them while moving on to the cart page.
Here a button should also be present which can be used to place the order. Send the request to
the server using this link :
<http://13.235.250.119/v2/place_order/fetch_result/>.
The parameters which you need to send to the server are the user_id, res_id and a JSON array
of food_id.
After receiving the confirmation from the server, send a notification to the user that their order
has been placed and redirect them to the ‘all restaurants’ page which will be your homepage.
 
My Profile
This page opens up from the navigation drawer. You need to put your details i.e. Name, Phone
number, and Address. You can choose your own design for the screen. However, these details
will not be editable.
Favorites
This page will contain the list of the restaurants which were marked as a favourite by you. You
need to fetch them from the local database. The functionality of this page will be the same as
the all restaurants screen and the remaining process will remain the same.
Order History
This page will contain the list of the food items you have previously ordered, arranged in
reverse chronological order. The details to be provided on this page are:
1. Restaurant name
2. Food items list
3. Cost of each item
The previous order data needs to be fetched from the server using the link :
<http://13.235.250.119/v2/orders/fetch_result/user_id>
Frequently Asked Question(FAQ) page
This page will contain a static list of questions. It is up to you as to what questions you want to
put there. This page will contain static data i.e. some questions and answers. You can hardcode
these questions and answers.
Logout
This will be an option provided in the navigation drawer to log out of the application. This will
be a simple log out which redirects the user to the login page while clearing all the preferences
stored. Make sure that after logout, if the user presses the back button then the app should exit
and not take the user back to the home page.
All the best!
