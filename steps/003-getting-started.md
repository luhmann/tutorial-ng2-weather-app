# Getting Started

So we now have a project setup that should be suitable for our purposes. If you have not already done so, 
revert the ejection of the app to its prior state. 

So lets have a look at what we want to build:

![Screens](../assets/screens.png)

In every development work no matter if backend or frontend you begin by conceptually breaking down the app
into smaller parts. This serves multiple purposes: First it makes the work better organizable. This is usually expressed
in user stories and what you do in groomings and plannings. Second the the structure you find usually will also often serve
as the organizing principle of your code.  It will aso help you in not repeating yourself as you identify components 
that appear in more than one place.

Think for a moment about how you would structure an app like this.

In frontend development you usually have some form of visual design, when you start developing a new app. This is a good
starting point for the breakdown process. 
Within the screenshot above we can see two different screens of this app: 

* One on the left which shows you the weather information for a single city, in this case Berlin
* The other which is a list of cities just showing the name of the city, the current local time and the current temperature

The two screens share no elements in exactly the same configuration, so we can assume that they are different "pages".
In web development this usually means that we are going to use different URLs to access them. Different URLS are one 
useful high-level conceptually distinction naturally existent in a well conceptualized app, so you can use it to divide
your work. Below that level, it is a matter of separating different parts of any one page into user stories 
that fit within one sprint and are well defined. We also want to add to the app feature by feature instead of releasing 
half-finished work. So we will not separate for example writing the markup and writing the styles.

The top-left area of the left screen seems like a good candidate for our first unit of work: 

![First Step](../assets/weather_for_city_current.png)

To break it down we can use one the basic conceptual building blocks of modern frontend-development: components. A component
is a part of a user interface that you can potentially use in more than one place. Whenever you can reuse a component
you increase your changes for greater consistency across your interfaces. And every modern frontend framework is structured
around components. Angular is no exception. If you want to know more about the general concept,
you can read a good introduction here: https://derickbailey.com/2015/08/26/building-a-component-based-web-ui-with-modern-javascript-frameworks/

Possible components we can identify in this part of the app are:

* `<weather-mood>`: The background displaying a fullscreen impression of the current weather situation (might be animated)
* `<city>`: The text "Berlin"
* `<weather-description>`: The text "Teilweise bewölkt"
* `<degrees>`: The text "19°"
* `<weather-shortinfo>`: The combination of <city>, <weather-description> and <degrees>

(If you do not like the names feel free to use better ones)

We can also already identify how we me might reuse some of these components in other areas of our interface:

![First Step](../assets/screens_reuse.png)

The `<weather-shortinfo>`-component from above highlights another very important concept: composability. 
Just like traditional HTML-Tags you can nest components into each other and create new components of increasing specificity. 
This allows a very granular approach to structuring your frontend-apps and allows for different levels of reusability. 
The `<city>`-component might be highly reusable, because in 
essence it represents just a very particular way of formatting a text (3rem Helvetica Neue light in a white color
and with a drop shadow), while the `weather-shortinfo`-component might potentially only exist in one place within your
app, as it is composed of three other components. 

**Task**
Build the five components mentioned above and make them display the current temperature and weather in Berlin

**How to do it**

* You will need an API to get the weather data. We will use https://openweathermap.org/api. 
* You are going to need an API key, so sign up for one http://openweathermap.org/appid
* All the data you need is provided by this endpoint: https://openweathermap.org/current
* Build a service that has a method for requesting and storing the weather for a single city from the API.
* Build the components mentioned above and style them for now to look like the screenshot as closely as possible. For the
`<weather-mood>`-component you can look for some nice pictures from https://unsplash.com/. They are free to use.
