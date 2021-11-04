# Lab 7 - Starter Code

# Lab 7 Notes

## **Concepts**

### Web Site Vs Web App
    - Thinking of it plainly, a website is catered towards delivering information to users, and providing a hub that directs users to different resources/web pages. It is much less focused on giving software functionality to perform tasks. A web app, however, is much more concerned with delivering software functionality than just plain content alone. 
    - Web Site == delivery of information and resources
    - Web App == Software Functionality
    - When a user uses a web app, they care more about how well the application carries out the tasks that it is designed to perform through its interactivity and performance, thus we have to consider this heightened interactivity and functionality as part of our requirements. 

### Web Site Dev Vs Web App Dev
    - Although this is all fine and dandy, having the browser load a new html page every time the user wants to perform an action is a little inefficient and quite slow. But recall that for a web site, the user is doing more reading and less clicking, so we can get away with these slower transitions. Furthermore we don’t have to worry about distributing our data among a bunch of different HTML files, since the user isn’t constantly interacting, creating, updating, and deleting data when moving through a website.
    - However with your recipe apps we expect heavy user interaction. This means potentially lots of CRUD actions and / or dynamic screens. The time it takes to load entire HTML files whenever we want to navigate just isn’t gonna cut it, especially when we are under resource constraints like a slow network or a weak browser, especially for mobile devices. 
    We have tools in JavaScript to help us with this problem. Using these tools, we can build what is known as a **single page application**.

### Single Page App (SPA)

Dynamically rewrites the current webpage from the server. Swap out html templates from a single file to give off perception of loading different websites.

### SPA needs 3 things
#### Routing system
  - Window.location (Holds current page url)
#### Browser History
  - History API
  - We need to manually change states to because the SPA isn't actually loading new websites.
  - Stores user history as a stack with pointer
  - back arrow decrements pointer
  - forward arrow increments pointer
  - If the user navigates to a new page while the browser history pointer is not at the top of the stack the stack from the pointer up will be popped off
  #### Windows event pop state listener tool
  - window.addEventListener('popstate', function(event) {})
  - Event object passed into call back function 
  - Event triggerd when user presses back arrow
  - Stores information about what History pointer is pointing too not current state
  #### history.pushState(state, title, url)
  - pass empty title
  - url should be url of page user is navigating to
  - State object is not used by browser it is for us to know which page to load when user hits back arrow
  - Use pop state object to know which view to show user when they hit the back arrow
#### Setup and Cleanup
  - Using document selectors and editing attributes

## Service Workers

We can't control the internet so how can we make our apps less network       dependant. Service workers are tools that allow us to circumvent this issue and allow our app to do more with less internet. Service Workers store recent calls locally so you don't have to use the internet to load new shit as it is stored locally. Service workers are stored within the browser.

- Register: This is in sw.js file and tells the javascript file which service worker to use for the app
- Install: Event listener and is triggered after succesful Register step
- Activate: This event is triggered anytime a change is made to the service worker
- Fetch: This returns the response on a cache hit
- Cache hit Vs Cache miss
  - Cache hit: Occurs when service worker has seen an internet request before, on hit pull data in response on last request.
  - Cache miss: When web application makes an entirely new request and we need to save the data, on miss store newtowrk response and request inside browser storage to use for later.
