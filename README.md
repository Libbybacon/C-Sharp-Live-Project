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
I created the partial view "_Comment" that represents individual comments.  It includes data attributes (commentPath and commentID) s
I created a partial view named "_Comments" that can be used to display an ordered-by-date list of all comments in the database on any page.
 
 ### Like/Dislike Implementation
 I added two methods to the Comments controller, one for adding likes and one for dislikes to comments. I created 
an ajax method for the like and dislike buttons that is called when the button is clicked that works with the controller 
methods to asynchronously add a like or dislike to each comment when the button is clicked and display the updated 
number of total likes or dislikes in the view.
 
 ### Like/Dislike Ratio Bar
 I added a bootstrap progress bar to the comments to reflect the percentage of likes each comment has. I altered the 
comments controller methods AddLike() and AddDislike() so that each returns a Json object containing the comment's likes 
(or dislikes) and the like ratio. I updated the Ajax methods so that each time a comment is liked or disliked the progress
 bar displays that change.
 
 ### Delete Button, Modal, Confirmation
I added an event listener to the trashcan icon on each comment so that it opens a confirm delte modal when clicked instead of routing the user to another page.  When the user clicks the confirm delete button in the modal, the comment's height is reduced until it disappears, the comment is deleted from the database, and a green delete confirmation badge is displayed for three seconds.

 
 ### Create & Reply Functionality
I replaced the 'Create new comment' action link with a form above the list of comments where users can enter text and submit it to create a new comment that appears at the top of the list.
I created a partial view for individual comments
I used jQuery Ajax to create methods that are functional without refreshing the page first for:
- Comment button - creates a new comment, adds that comment to the page and erases the text in the  
   input field
- Like button - changes number of likes next to the like button and adjusts the like/dislike ratio bar
- Dislike button -changes number of dislikes next to the dislike button and adjusts the like/dislike ratio bar
- Trashcan icon button - brings up delete confirmation modal
- Reply button - displays form below comment who's reply button user has clicked
- Cancel button in reply form - hides reply form
- Reply comment submit button - creates new comment, displays new comment at top of list, hides reply form


// New Comment Event
const newCommentEvent = (e) => {
    var message = $("#commentMessage").val();
    var path = e.target.getAttribute("data-CommentPath");
    //Sends input text to Create method in controller which creates a new comment in the Db with text input as comment Message
    $.ajax({
        type: "POST",
        url: path,
        data: { message: message },
        success: function (result) {
            //Replace input text with placeholder text
            $("#commentMessage").val(null);
            var jQueryResult = $(result);
            // Add like
            jQueryResult.find('.likeBtn').click(addLikeEvent);
            // Add Dislike
            jQueryResult.find('.dislikeBtn').click(addDislikeEvent);
            // Click Trashcan
            jQueryResult.find('.trashcan').click(trashcanEvent);
            // Click Reply - show form
            jQueryResult.find('.replyBtn').click(replyEvent);
            // Add New Reply Comment - submit new reply comment
            jQueryResult.find('.replySubmitBtn').click(newReplySubmitEvent);
            // Cancel Reply - hide form
            jQueryResult.find('.cancelReplyBtn').click(cancelReplyEvent);
            // Add new comment to top of the list
            $(".newComment").prepend(jQueryResult);
        },
        error: function (request, status, error) {
            serviceError();
        }
    });
}


 
 ## Front End Stories
I added front-end design following the client's color and styling guidelines.







