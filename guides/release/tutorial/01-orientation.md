<!-- Heads up! This is a generated file, do not edit directly. You can find the source at https://github.com/ember-learn/super-rentals-tutorial/blob/master/src/chapters/01-orientation.md -->

You can install the latest version of _Ember CLI_ by running the following command. If you've already done this by following the [Quick Start](../../getting-started/quick-start/) guide, feel free to skip ahead!

```shell
$ npm install -g ember-cli
```

To verify that your installation was successful, run:

```shell
$ ember --version
ember-cli: 3.12.0
node: 12.8.1
os: linux x64
```

If a version number is shown, you're ready to go.

We can create a new project using Ember CLI's `new` command. It follows the pattern `ember new <project-name>`. In our case, the project name would be `super-rentals`:

```shell
$ ember new super-rentals -b @ember/octane-app-blueprint
installing octane-app-blueprint
  create .editorconfig
  create .ember-cli.js
  create .eslintignore
  create .eslintrc.js
  create .template-lintrc.js
  create .travis.yml
  create .watchmanconfig
  create README.md
  create app/app.js
  create app/index.html
  create app/resolver.js
  create app/router.js
  create app/styles/app.css
  create app/templates/application.hbs
  create config/environment.js
  create config/optional-features.json
  create config/targets.js
  create ember-cli-build.js
  create .gitignore
  create jsconfig.json
  create package.json
  create public/robots.txt
  create testem.js
  create tests/index.html
  create tests/test-helper.js
npm: Installing dependencies ...
npm: Installed dependencies
Successfully initialized git.
```

This should have created a new folder for us called `super-rentals`. We can navigate into it using the `cd` command.

```shell
$ cd super-rentals
```

For the rest of the tutorial, all commands should be run within the `super-rentals` folder. This folder has the following structure:

```plain
super-rentals
├── app
│   ├── styles
│   │   └── app.css
│   ├── templates
│   │   └── application.hbs
│   ├── app.js
│   ├── index.html
│   ├── resolver.js
│   └── router.js
├── config
│   ├── environment.js
│   ├── optional-features.json
│   └── targets.js
├── public
│   └── robots.txt
├── tests
│   ├── index.html
│   └── test-helper.js
├── tmp
├── .editorconfig
├── ember-cli-build.js
├── .ember-cli.js
├── .eslintignore
├── .eslintrc.js
├── .gitignore
├── jsconfig.json
├── package.json
├── README.md
├── .template-lintrc.js
├── testem.js
├── .travis.yml
├── .watchmanconfig
└── yarn.lock

7 directories, 26 files
```

We will get to know the purposes of these files and folders as we go. For now, just know we will spend most of the time working within the `app` folder.

Ember CLI comes with a lot of different commands for a variety of development tasks, such as the `ember new` command that we saw earlier. It also comes with a _development server_, which we can launch with the `ember server` command:

```shell
$ ember server
Could not start watchman
Visit https://ember-cli.com/user-guide/#watchman for more info.
building... 

Build successful (9761ms) – Serving on http://localhost:4200/
```

The development server is responsible for compiling our app and serving it to the browsers. It may take a while to boot up. Once it's up and running, open your favorite browser and head to <http://localhost:4200>. You should see the following welcome page:

<img src="/screenshots/01-orientation/welcome@2x.png" alt="Welcome to Ember!" width="1024" height="596">

<div class="cta">
  <div class="cta-note">
    <div class="cta-note-body">
      <div class="cta-note-heading">Zoey says...</div>
      <div class="cta-note-message">
        <p>The <code>localhost</code> address in URL means that you can only access the development server from your local machine. If you would like to share your work to the world, you will have to <em>deploy</em> your app to the public Internet. Don't worry, we will cover that in Part 2 of the tutorial.</p>
      </div>
    </div>
    <img src="/images/mascots/zoey.png" role="presentation" alt="Ember Mascot">
  </div>
</div>

You can exit out of the development server at any time by pressing `Ctrl + C` on your keyboard in the terminal where the server is running. We recommend having two terminal windows open: one to run the server in background, another to type Ember CLI commands.

The development server has a feature called _live reload_, which monitors your app for file changes, automatically re-compiles everything, and refreshes any open browser pages. This comes in really handy during development, so let's give that a try!

As text on the welcome page pointed out, the source code for the page is located in `app/templates/application.hbs`. Let's try to edit that file and replace it with our own content:

```handlebars { data-filename="app/templates/application.hbs" data-diff="-1,-2,-3,-4,-5,-6,+7" }
{{!-- The following component displays Ember's default welcome message. --}}
<WelcomePage />
{{!-- Feel free to remove this! --}}

{{outlet}}

Hello World!!!
```

Soon after saving the file, your browser should automatically refresh and render our greetings to the world. Neat!

<img src="/screenshots/01-orientation/hello-world@2x.png" alt="Hello World!!!" width="1024" height="250">

When you are done experimenting, go ahead and delete the `app/templates/application.hbs` file. We won't be needing this for a while, so let's start afresh. We can add it back later when we have a need for it.

Again, if you still have your browser tab open, your tab will automatically re-render a blank page as soon as you delete the file. This reflects the fact that we no longer have an application template in our app.

Create a `app/templates/index.hbs` file and paste the following markup.

```handlebars { data-filename="app/templates/index.hbs" }
<div class="jumbo">
  <div class="right tomster"></div>
  <h2>Welcome to Super Rentals!</h2>
  <p>We hope you find exactly what you're looking for in a place to stay.</p>
</div>
```

If you are thinking, "Hey, that looks like HTML!", then you would be right! In their simplest form, Ember templates are really just HTML. If you are already familiar with them, you should feel right at home here.

Of course, unlike HTML, Ember templates can do a lot more than just displaying static content. We will see that in action soon.

After saving the file, your browser tab should automatically refresh, showing us the welcome message we just worked on.

<img src="/screenshots/01-orientation/unstyled@2x.png" alt="Welcome to Super Rentals! (unstyled)" width="1024" height="250">

Before we do anything else, let's add some styling to our app. We spend enough time staring at the computer screen as it is, we must protect our eyesight against unstyled markup!

Fortunately, our designer sent us some CSS for us to use, so we can just go ahead <a href="/downloads/style.css" download="app.css">download the stylesheet file</a> and copy it into `app/styles/app.css`. This file has all the styles we need for building the rest of the app.

```css { data-filename="app/styles/app.css" }
@import url(https://fonts.googleapis.com/css?family=Lato:300,300italic,400,700,700italic);

/**
 * Base Elements
 */

* {
  margin: 0;
  padding: 0;
}

body,
h1,
h2,
h3,
h4,
h5,
h6,
p,
div,
span,
a,
button {
  font-family: 'Lato', 'Open Sans', 'Helvetica Neue', 'Segoe UI', Helvetica, Arial, sans-serif;
  line-height: 1.5;
}

body {
  background: #f3f3f3;
}

/* ...snip... */
```

If you are familiar with CSS, feel free to customize them to your liking! Just keep in mind that you may see some visual differences going forward, if you choose to do so.

When you are ready, save the CSS file; our trusty development server should pick it up and refresh our page right away. No more unstyled content!

<img src="/screenshots/01-orientation/styled@2x.png" alt="Welcome to Super Rentals! (styled)" width="1024" height="250">

To match mockup from our designer, we will also need to download the `teaching-tomster.png` image, which was referenced from our CSS file:

```css { data-filename=app/styles/app.css }
.tomster {
  background: url(../assets/images/teaching-tomster.png);
  /* ...snip... */
}
```

As we learned earlier, the Ember convention is to place your source code in the `app` folder. For other assets like images and fonts, the convention is to put them in the `public` folder. We will follow this convention by <a href="/downloads/teaching-tomster.png" download="teaching-tomster.png">downloading the image file</a> and saving it into `public/assets/images/teaching-tomster.png`.

Both Ember CLI and the development server understand these folder conventions and will automatically make these files available to the browser.

You can confirm this by navigating to
`http://localhost:4200/assets/images/teaching-tomster.png`. The image should also show up in the welcome page we have been working on. You may need to do a manual refresh for the browser to pick up the new file.

<img src="/screenshots/01-orientation/styled-with-tomster@2x.png" alt="Welcome to Super Rentals! (with Tomster)" width="1024" height="250">