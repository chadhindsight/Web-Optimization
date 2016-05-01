# Website Performance Optimization Portfolio Project

This Project Contains two parts.
 1. We are supposed to optimize a given portfolio page to achieve a score of 90 or above on google page insight.
 2. We are supposed to optimize the FPS on a page to run at silky smooth 60FPS.

##Optimizing the Portfolio Page to achieve a page insight score of 90+.

###Link to Optimized Page:
http://prateekcoder.github.io/Front-End-Nanodegree-P4-Website-Optimization/

####The page insight Score of the Portfolio initially:
The page provided to me had a very poor page insight score of 28 for mobile view and 30 for desktop view.

![alt](http://s22.postimg.org/ick38se4x/Mobile_View_Before.png)

![alt](http://s18.postimg.org/ylprqhwo9/Desktop_View_Before.png)

####First Optimization (Image Optimization):
The very first Optimization I did was the Image Optimization, Images takes up almost 95% of the data which are being downloaded by the clent, so images are the most critical things towards our Critical Path Optimization part. I customized 2 images namely the profilepic and the pizzeria.jpg. Reducing pizzeria.jpg to 18% of its original size helped in reducing the image from 2.25mb to a whooping 129kb. Further to achieve better optimization I converted the image format from jpg to webp, which further helped me reduce the image size from 129kn to 75.1kb, finally helping me compress the image appox. by 97%-98%. I did all the image optimization using ImageMagick cli tool. I also optimized the profilepic and converted into webp format.
Here is the result from page insight after Image Optimization:

![alt](http://s22.postimg.org/m4looxh1t/Mobile_View_Image_Optimization.png)

![alt](http://s7.postimg.org/kx7udxuh7/Desktop_View_Image_Optimization.png)

####Second Optimization (Google Font and perfmatter.js):
The second optimization was the JavaScript optimization and the external link to google font optimization. Since the JS file was not a very big file, the best optiion was to just inline that in the script tag and make it async so that it does not block the rendering process and I also made the Google analytics JS async so that it does not block the rendering process. Instead of creating a new link tag which took extra time while rendering for fetching the google font API, I attached it with href in the same styles.css link tag to stop it from taking extra amount if time while rendering.
Here is the google page insight result after Google font and JS optimization:

![alt](http://s28.postimg.org/xbv1a0b4t/Mobile_View_After_Google_Font_Optimization.png)

![alt](http://s10.postimg.org/8vzz595uh/Desktop_View_After_Google_Font_Optimization.png)

####Final Optimization (CSS Optmization):
There were three css files, which I optimized:
 1. print.css : This file needs to be only called when we want to print the page, so I optimized it using the media tag, in the link I used media and used print so that it is only going to be called when we want to print the page. Further since the print.css code were very less to further optimize I inlined the codes in the html file inside the style tag.
 2. portraitscreen.css : This code was written inside style.css but I made another file for this code, since it was supposed to be called only when the orientation of the device is potrait and the max-width is 480px. Since there were very few lines of codes I inlined this code again inside the style tag and used the media, which stated it is only going to be used when the orientation is portrait and the max-width of the device is 480px.
 3. styles.css : This file was supposed to be used everytime so using any kind of media was not a good idea, but the codes in this file were not very large and it was a good idea to just inline the codes. So I inlined the style.css file code to html inside the style tag.

After all these optimization I was finally able to achieve a google page insight score of 90+. Here is the snap of the final insight score after all the optimizations:

![alt](http://s22.postimg.org/4y7xfi5ch/Final_Mobile_View_Page_Speed.png)

![alt](http://s16.postimg.org/o5fhozd39/Final_Desktop_View_Page_Speed.png)

###Optimizations which were out of the Scope:

 1. Leverage Browser Caching: Since I was working on github, and I had a github project page, instructing the browser for the max age for particular files was not possible since caching process and intructions to the web browser can be given by making changes to the .htaccess files but Github don't let the user access those files due to security puposes, so this optimization was out of my scope.
 2. Reduce Server time: Even this thing was out of my scope because of the github project page. My server response time was 0.24 seconds.

##Optimizing Pizza.html to achieve a frame per second rate of 60 or higher:

##FPS rate of pizza.html initially:
![alt](https://s10.postimg.org/w1l8e7t49/Before.png)

Using Chrome Developement Tools and loading the original pizza.html in an icognito mode shows the following loading times and number of frames in the console:

Average time to generate last 10 frames: 36.56720000290079ms FPS: Way over 60 FPS

##Optimizations done in JavaScript:
 * Replaced "querySelector" with "getElementById", since the selectors are not too complex I chose getElementbyId since it is less expensive.
 * Replaced "querySelectorAll" with "getElementsByClassName", since querySelector is also way too expensive for its desired purpose on pizza.html.
 * Created a new variable allPizzaContainers for all pizza containers to apply dx and newwidth to all pizza containers; placed all variables out of the for loop.
 * Placed the variable pizzasDiv in the for loop outside the for loop.
 * Added createDocumentFragment to create a imaginary node to append its values to the pizza.html, reduced the number of Pizzas to the media size and the max of pizzas to 100.
 * Added caching to actually cash items and if cashed to return the cached items.

##Optimizations done in CSS:
 * Added width and style of Pizzas to style.css, in CSS also manipulated backface-visibility since it is a visual property, that will cause painting to occur. Painting is obviously a super expensive operation in this project.
 * In CSS I also added transform to force hardware acceleration.

##Final Result After Optimizations:
![alt](https://s18.postimg.org/5q5rrpwd5/After.png)

Yes that's 60fps. Now the webpage is rendering at a silky smooth 60fps or higher.


##Intructions By Udacity.
Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js.

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
