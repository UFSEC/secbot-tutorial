# SECbot tutorial!
Welcome to this slackbot tutorial! Today we're going to be using some interesting tools and softwares like **Node JS**, **Heroku**, and the **Slack API**.

## Prerequisites
* I use the command line very heavily in this tutorial so a basic familiarity with it is not required but recommended. I highly encourage you to watch our awesome [Command Line Wizardry tutorial](https://youtu.be/EKJZ6Gc19OI) before starting this tutorial
* If ```(Windows.user() == true)``` please install [git bash](https://git-for-windows.github.io/)!
* Have a text editor installed such as [Atom](https://atom.io/)
* Install [Node](https://nodejs.org/en/). If you have a Mac you can install [Homebrew](https://brew.sh/) and then just run ``` brew install node ``` in the terminal
* Create a Slack workspace [here](https://slack.com/get-started#create)
* Create a Heroku account [here](https://signup.heroku.com/dc)
* Install the Heroku toolbelt [here](https://devcenter.heroku.com/articles/heroku-cli)

#### That's A LOT

If you get stuck installing anything or you're not sure what commands we're doing at any given point feel free to email/message me to see if we can get it working!

## Introduction to Slack and Slackbots

Slack is an awesome team messaging platform for people who want to be efficient and smart about the way they communicate. It has a ton of customization features and it's very developer friendly!

Today we're going to be creating a Slackbot which will respond to trigger words

Overall, we're going to be creating a simple bot written in NodeJS, running on an Express server, and pushed to Heroku.

## Let's start by creating a folder to contain all of this

#### package.json file
The "JavaScript Object Notation" syntax is what is used in json files to store and send data to and from servers.
package.json files serve as documentation for what packages your project depends on, allows you to specify the versions of a package that your project can use, and makes your build reproducible

The lovely documentation from [npmjs.com](https://docs.npmjs.com/getting-started/using-a-package.json) goes more into detail regarding package.json files if you're curious


``` javascript
{
  "name": "secbot",
  "version": "0.0.1",
  "description": "our bot!",
  "main": "app.js",
  "author": "Devy D. Developer",
  "license": "MIT",
  "dependencies":
  {
    "express": "^4.x.x",
    "body-parser": "^1.x.x",
    "request": "2.56.x"
  }
}

```

#### NPM

NPM is called a Node Package Manager. It basically helps you install all the packages you need for any module (JS libraries) in NodeJS.
[npmjs.com](https://www.npmjs.com/) has amazing documentation and different packages you can install.

Go ahead and run these two commands in your command line (making sure you're in the folder where the package.json file is located)

```
npm install
```
 ```
 npm install slackbots
 ```

#### app.js

Next we're going to create our javascript file which will contain most of the logic of our slackbot

First, we're creating variables to import/include the Node modules we'll be needing like express, bodyParser, and slabot.
Then, we're creating a var to contain the function for express, the server to host our code, and the slackbot.
Then, we're using an express method to parse the data //TODO
Lastly, we're printing to the console to let us know our program is running

```javascript
//require is like import/include
//var slackbot = require('slackbots');
var express = require('express');
var bodyParser = require('body-parser');

var app = express();
var port = process.env.PORT || 1337;
//var bot = new slackbot({
//   token: 'YOUR_TOKEN_HERE', // Add a bot https://my.slack.com/services/new/bot and put the token
//    name: 'My Bot'
//});
//bot.on('start', function(){
//  var params = {
//    icon_emoji: ':triumph:'
//  };

//  bot.postMessageToChannel('general', 'SEC is the BEST', params);
//});

// body parser middleware
app.use(bodyParser.urlencoded({ extended: true }));

// Hello world test
app.get('/', function (req, res) { res.status(200).send('Hello world!'); });

app.listen(port, function () {
  console.log('Listening on port ' + port);
});
```


#### Checkpoint!

Run your app by going to your command line and typing in

```
node app.js
```
It should print

```
Listening on port YOUR_PORT_HERE
```

Then open a new window and type in this simple bash command to grab information given a url

```
curl 'localhost:YOUR_PORT_HERE/'
```
### Let's create our Slackbot!


```javascript


//once a POST request is received at /hello
app.post('/hello', function (req, res, next) {
    //extract information about the user which created the request
  var userName = req.body.user_name; //request for username
  var botPayload = {
    text : 'Hello ' + userName + ', welcome to UF SEC Slack channel!'
  };
  // loop
  if (userName !== 'slackbot') {
    return res.status(200).json(botPayload); //json response to be sent to slack
  } else {
    return res.status(200).end();
  }
});

```
### Heroku!!!

platform as a service (PaaS) that enables developers to build, run, and operate applications entirely in the cloud.

Up until now our bot operates only locally. In order to get it connected to the internet we need heroku to create a server to run our app
I hope by now that you already have your heroku account created, if not do this now! Also make sure you have the Heroku cli tool installed as well!

To create a heroku app we need what's called a **Procfile**.

"A Procfile is a mechanism for declaring what commands are run by your application’s dynos on the Heroku platform. It follows the process model. You can use a Procfile to declare various process types, such as multiple types of workers, a singleton process like a clock, or a consumer of the Twitter streaming API."
 [Here](https://devcenter.heroku.com/articles/procfile) are some more details in case you're curious.

Create a new file, name it Procfile and just write

```
web: node app
```

In order to push our code to the heroku app we need to run the following git commands:

```
git init
git add .
git commit -m "Initial commit"
```
Then type these commands out:
```
heroku create
git push heroku master
```
If this is you first time doing this I believe it will prompt you to enter your username and password.

#### Checkpoint!

If the commands were successful you should have a url where the app is launched. Go to the url and it should say "Hello World!"


### Slack configurations

Navigate to your slack workspace and go to Customize. After you are there use the search bar to find "Outgoing Webhooks". Configure a new hook.

We want to set a trigger word and the url it corresponds to. Write your trigger word and append the "/hello" to the end of it so it can route to the POST we want it to use.

If you go to your workspace now when you type the trigger word your slackbot should respond accordingly.

Everytime someone mentions the trigger word, Slack is able to route to the path we specified and receive the JSON data from it.


## Join our Slack at ufsec.slack.com !


## Challenge Time!

Have you heard of [IBM Watson](https://www.ibm.com/watson/)?

"Watson is a question answering computer system capable of answering questions posed in natural language"

Watson has a module called "Conversation" which users can interact with through an interface (ie. Slack). It's very easy to set up and work with - it's basically all through a GUI on IBM's website and the documentation is awesome. There's a lot of room for creativity and exploration! Here's two fun examples of how I was able to use Conversation:

![](/img/blackbear.png)

![](/img/kanye.png)

Begin by making an account on [Bluemix](https://www.ibm.com/cloud-computing/bluemix/).

[Here's](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted) how you get started with your first Conversation workspace!

Email or facebook message me your completed challenge or any other ways you get creative and you'll get mad brownie points :sparkles:

With your permission, we can even feature your creations on our Facebook and website!
## Helpful links, tips, and sources

## Thanks for following along!
My name is Daniela and my email is dtravie@gmail.com if you have any questions or comments
