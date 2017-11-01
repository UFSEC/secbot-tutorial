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
