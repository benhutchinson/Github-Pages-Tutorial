Introduction To AJAX Technology
===============================

In this project, we learnt about AJAX browser technology and how to integrate JSON data objects from third parties within a web-page. This project involves pulling in user-profile data from Github's API.  A central search field allows the user to search through GitHub usernames and on submission, data regarding the user's number of repos and commits is published on the page.  Due to the structure of Github's API, 3 data sources are referenced in order to populate the page with the desired data.  To account for different connection speeds and to provide for a better user experience, jQuery is deployed to show a spinner graphic while the data is sourced.  In terms of design, the background makes use of an SVG file; the advantage of SVG files is that they can be scaled to infinite proportions without any sacrifice of visual quality.  The project [can be found here](https://pure-coast-6680.herokuapp.com).  In future, I would like to improve the design and learn more about SVG.

###Code Extract
```Javascript
function addProfileFromUsername(username){
  $('.spinner').show();
  $.get('https://api.github.com/users/'+ username + "?client_id=<%=ENV['CLIENT_ID']%>&client_secret=<%=ENV['CLIENT_SECRET']%>", function(user){
      renderTemplate(user, username);
    })
  .error(function(){
    $('.modal').addClass('shown');
  })
  .always(function(){
    $('#username').val('');
    $('.spinner').hide();
  })
}
```

###Core Technologies
- Sinatra
- jQuery & Javascript
- SVG
- Basic HTML/CSS