# C# Live Project

![Comments - My ASP NET Application](https://user-images.githubusercontent.com/56324316/116736762-4fa49a80-a9be-11eb-8814-130c2b0d98a4.gif)
 
## Introduction
 During my final two weeks at the Tech Academy, I worked with my peers within an Agile Framework to help create an MVC web application for a Portland-based theater company using Visual Studio, C# and the .NET Framework.  I had the option to select one of three areas of focus at the beginning of our two week sprint, and I chose to tackle the Comments page because I hoped to focus more on back end logic versus front end design.  Over those two weeks I was assigned several stories that tasked me with adding asynchronous functionality to various aspects of the comments.  I had almost no experience working with jQuery or Ajax before this project, but I learned an incredible amount in a very short time and I am very pleased with the results.
 
 ## Back End Stories
 - Comments Partial View
 - Like/Dislike Implementation
 - Like/Dislike Ratio Bar
 - Delete Button, Modal, Confirmation
 - Create & Reply Functionality
 
 ### Comments Partial View
I created a partial view named "_Comments" that can be used to display an ordered-by-date list of all comments in the database on any page.
 
 ### Like/Dislike Implementation
 I added two methods to the Comments controller, one for adding likes and one for dislikes to comments. I created 
an ajax method for the like and dislike buttons that is called when the button is pushed that works with the controller 
methods to asynchronously add a like or dislike to each comment when the button is pushed and display the updated 
number of total likes or dislikes in the view.
 
 ### Like/Dislike Ratio Bar
 I added a bootstrap progress bar to the comments to reflect the percentage of likes each comment has. I altered the 
comments controller methods AddLike() and AddDislike() so that each returns a Json object containing the comment's likes 
(or dislikes) and the like ratio. I changed the ajax methods so that each time a comment is liked or disliked the progress
 bar displays that change.
 
 ### Delete Button, Modal, Confirmation
 -Instead of takin User to Delete page, have delete button open confirmation modal
-Ask user if they are sure they want to delete this comment
-Modal should have a confirm button and a cancel button
-Clicking confirm button should:
	-delete comment without reloading the page(ajax)
	-hide deleted comment on page
	-display fixed message at top of page that says "comment was deleted successfully" if comment was.
-popup message when comment is delted should have green theme and font-awesome checkmark at the end
-popup message should ppear and stay on screen for 3 seconds then fade out and disappear

Changed comment delete button so that it opens a confirm delete modal with confirm and cancel buttons instead of routing to another page. 
 Created an ajax method that deletes the comment, removes it from the page, and displays a green confirmation for 3 seconds.
 
 ### Create & Reply Functionality
 -add implementation for user to create and reply to comments w/out navigating to another page.
-replace Create New link w/ short form that let's user type message
-Clicking reply button for comment brings up that form directly below that comment
-sort comments in _comments partial view so most recent comments appear first
-creating new comment should not refresh page
-use ajax to add new comment to page when new comment or reply comment is created

make create method in controller void

-Added form with a text input above the list of comments where users can add a new comment.
-Added Ajax function to newComment button that creates a new comment and deletes the text from the input box (doesn't refresh list though).
-Added function to cancel button that clears text from input box.
-Changed the return in the Index method in the comments controller to a list of comments sorted in descending order by comment date, 
 so most recent comments appear first
-Created partial view _Comment for individual comments

I replaced the 'Create new comment' action link with a form above the list of comments where users can enter text and submit it to create a new comment that appears at the top of the list.
I created a partial view for individual comments
I used Jquery Ajax to create methods that are functional without refreshing the page first for:
 -Comment button - creates a new comment, adds that comment to the page and erases the text in the  
   input field
-Like button - changes number of likes next to the like button and adjusts the like/dislike ratio bar
-Dislike button -changes number of dislikes next to the dislike button and adjusts the like/dislike ratio bar
-Trashcan icon button - brings up delete confirmation modal
-Reply button - displays form below comment who's reply button user has clicked
-Cancel button in reply form - hides reply form
-Reply comment submit button - creates new comment, displays new comment at top of list, hides reply form
 
 ## Front End Stories

CREATE COMMENT MODEL & CRUD PAGES

Created a Comment model in the blog area
Added that model db set to ApplicationDbContext definition in IdentityModels
Created controller and scaffolded CRUD pages for the Comment model
Removed Likes, Dislikes & CommentDate from Create and Edit views
Changed css for some buttons and text to make it more readable for user


IMPLEMENTING COMMENT FEATURES PT 2: STYLING THE COMMENTS
Reformatted comment display to include comment's author, time since comment was posted and the user's message.  
Added like and dislike buttons and display the number of each.
Added reply button
Added trashcan button







