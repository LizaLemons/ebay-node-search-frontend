# eBay Search app

##Links
- GitHub
	- [Frontend](https://github.com/LizaLemons/ebay-node-search-frontend)
	- [Backend](https://github.com/LizaLemons/ebay-node-search-backend)  
- Heroku
	- [Frontend](https://ebay-node-search.herokuapp.com/)
	- [Backend](https://ebay-node-search-backend.herokuapp.com/items?search=cats%20toys)  


##Technology used
* Backend
	- Node
	- Express
	- CORS
* Frontend
	- Angular
	- Bootstrap


##How it works

###Backend
The backend is built with Node, Express and CORS. It has one route ('/items'), which, when you pass the URL a query string (like '/items?search=cats%20toys'), will make an API call to eBay.

If you log the 'req', you can see it has a property of 'search'. I used this to compose the URL in the HTTP GET request to eBay's API. I used eBay's 'Finding' service and findItemsByKeywords call to return the top 10 most relevant results.

I also specified a script called 'server' that when called (using 'npm run server') uses Nodemon autoreloader so I wouldn't have to restart my server after every change.

###Frontend
The Angular frontend has one module with two properties - a controller and a service that makes the HTTP request to my Node backend's URL.

The controller contains the Angular submit fxn for the search input on the frontend. If there is text in the search box upon submit, the loading spinner changes from false to true and is displayed using 'ng-show'.

In the submit fxn is the eBayRequestService fxn, which performs the getItems fxn, passing it the searchTerms. This is how the frontend talks to the backend. It makes an HTTP GET request to the backend's URL.  

In the promise, I set the $scope's searchResults to data['item'] and set the spinner to false. Because now we're done loading and you no longer need to see a spinner.

In the HTML, I display the search results using 'ng-repeat'. This loops over the $scope's searchResults and displays each one. While in that loop, I display the current result's image, location and eBay URL. 

###Heroku
I decided to use Heroku to quickly host my site. This proved to be an interesting endeavor, but I learned a lot about pushing a Node app to Heroku, and about how to hack it so Heroku will accept a static site (my frontend).
