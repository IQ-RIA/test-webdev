# Review SaaS system

We would like to create a SaaS system for collecting reviews from the websites.  
This is a basic task, but think about this as about the first version of your startup. How would
you design it? What extension points you see?  
Assume that there is a system in place for adding and editing site accounts. Just create a DB
table and records in it.

##### The process is as follows:
1. Website admin gets his account and embeds JS code into his website.
2. This JS code renders a feedback button on the right side of the screen.
3. User clicks “Feedback” button on the right side of the screen
4. He gets a popup in the middle of the screen
5. On the first step of the popup he selects rating (1-5) and fills in the review itself.
6. On the second step the user fills in his contact details: First name, last name, email,
website, position, short bio.
7. All information goes to the central system. User gets “thank you” message and a
confirmation email (email is optional).
8. (optional) There should be an interface for the site admin to view all the reviews.
9. (optional) There should be an API call to get information about the reviews for the whole
system and for each website as follows:  
```/report?site=site.com``` -> all reviews grouped by rank

##### In more details, you need to do the following:
+ Implement bootstrap.js that is added to the target websites
+ Render the button on the right side of the screen
+ Click on the button opens dialog. The solution we know is iframe (because of the CSS,
JS conflicts and AJAX), but if you have other suggestions, let us know.
+ Implement first and second step with validation that makes sense.
+ Implement web-server exposing API method for submitting the feedback
+ Make sure that it is impossible to fake the script and let all users submit data from one
website in other’s account.
+ Optionally send a “thank you” email to the user
+ Optionally implement admin panel with the account owner login and list of reviews for his
website
+ Optionally implement API endpoint that provides report grouped by rank, for example (should be valid JSON):  
``` 
    { 
        5: [list of review texts],  
        4: [list of review texts],  
        //no 3  
        2: [list of review texts],  
        1: [list of review texts] 
    }
```
HTML/CSS for the frontend is provided in the repo, but feel free to modify it or not use it at all. This is just to save you time.
![alt tag](https://raw.github.com/XXimiCC/test-webdev/master/diagram.png)

##### We’ll evaluate the code from the following perspectives:
+ Completeness. It should work fine and process all errors correctly without unexpected
exceptions.
+ Clarity. Naming, files/folders structure, code style. It should not match ours, but it should
be consistent.
+ Structure. Object-oriented design on the backend and frontend.
+ DB. Design and queries.
+ Security. https://www.owasp.org/index.php/Top_10_2013-Top_10
