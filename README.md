# <img height="70px" src="assets/logo.svg" alt="JW Player Logo" title="JW Player Logo"/>

> Plays everywhere, every time.

Live on over 2 million sites with 1.3 billion unique plays per month, JW Player is the solution for seamless video playback across browsers and media types. It empowers the developer to interact with video programmatically to create unique and awesome user experiences.
  
## Disclaimer
This is the non-commercial version of JW Player. It does not contain the same features as the commercial-use player available from [jwplayer.com](https://www.jwplayer.com/). Commercial use and access to features requires a license. Learn more at https://www.jwplayer.com/pricing/. If you are a paid customer and want a player, please download it from the "Downloads" section of your JW Dashboard.
  
## Official Documentation
- [Developer Portal](https://developer.jwplayer.com/)
- [API Reference](https://developer.jwplayer.com/jw-player/docs/developer-guide/api/javascript_api_reference/) 
- [Configuration Reference](https://developer.jwplayer.com/jw-player/docs/developer-guide/customization/configuration-reference/)
- [Demos](https://developer.jwplayer.com/jw-player/demos/)
- [Support](http://support.jwplayer.com/)

## A Simple Example

The example below will render a video player into the div with the `player` id, listens to an event, and makes a few calls using the API.

````html
<!DOCTYPE html>
<html>
<head>
    <script src='LINK_TO_YOUR_PLAYER'></script>
    <script>jwplayer.key='YOUR_KEY';</script>
</head>
<body>
    <div id="player">Loading the player...</div>
    <script>
        // Setup the player
        const player = jwplayer('player').setup({
            file: 'LINK_TO_YOUR_FILE.mp4'
        });

        // Listen to an event
        player.on('pause', (event) => {
            alert('Why did my user pause their video instead of watching it?');
        });

        // Call the API
        const bumpIt = () => {
            const vol = player.getVolume();
            player.setVolume(vol + 10);
        }
        bumpIt();
    </script>
</body>
</html>
````

## Contributing

We appreciate all contributions towards the player! Before submitting an issue or PR, please see our contributing docs [here](CONTRIBUTING.md).

## Building the Player

We use `grunt` and a few `npm scripts` to build the player, lint code, and run tests. Debug code is built to `/bin-debug`, while minified & uglified code is built to `/bin-release`. Code is built with `webpack`, linted with `eslint`, and tested with `karma`, `mocha` and `chai`.

#### Requirements:

- [Node.js](http://nodejs.org/download/) with npm
- Install global npm dependencies
`npm install -g eslint grunt-cli jsdoc karma-cli stylelint webpack webpack-cli`

#### Steps:

1. Fork the project, clone your fork, and set up the remotes:
````bash
# Clone your fork of the repo into the current directory
git clone https://github.com/<your-username>/jwplayer
# Navigate to the newly cloned directory
cd jwplayer
# Assign the original repo to a remote called "upstream"
git remote add upstream https://github.com/jwplayer/jwplayer
````

2. Install the dependencies:
````bash
# Install dependencies
npm install -g eslint grunt-cli jsdoc karma-cli stylelint webpack webpack-cli
npm install
# Optionally, install webpack-dev-server
npm install -g webpack-dev-server
````
 
3. Build the player:
````bash
# Build once
grunt
# Complete Watch - builds JS, lints, and tests on each change
grunt serve
# Quick JS Watch - build only. Requires webpack-dev-server to be installed globally
webpack-dev-server -w --env.debug --port 8888 --output-public-path /bin-debug/
# Open the test page from another terminal window
open http://localhost:8888/test/manual/
````
 
4. Test your code:
````bash
# All browsers
grunt test
# Individual browsers - chrome, firefox, safari
grunt karma:{BROWSER} e.g. grunt karma:chrome
````
 
5. Lint your code:
````bash
npm run lint
````

6. Setup git pre-push hook
This will add a `pre-push` script to the project's .git/hooks folder that will lint and run unit tests on the branch before any push.
````bash
grunt hooks
```` 

## Framework Integration

While the JW team does not maintain any framework integrations of our own, there are developers in our community who do. We recommend the following libraries:

| Framework | Link |
| --------- | ---- |
| React |  https://github.com/micnews/react-jw-player |

If you have a library which you believe is good enough to meet the needs of other developers using a certain framework, please open a pull request modifying the above table.

## Software License

The use of this library is governed by a [Creative Commons license](http://creativecommons.org/licenses/by-nc-sa/3.0/). You can use, modify, copy, and distribute this edition as long as it’s for non-commercial use, you provide attribution, and share under a similar license.
http://www.jwplayer.com/license/
