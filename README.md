# Action API Tester

A plugin to listen to all the events in the Action API

## Motivation

When working with Sketch’s Action API, sometimes it’s hard to know which actions you should be listening to in your code. This plugin tries to solve that issue by listening for all the actions, and logging some details about them.

Ideally, you’ll just have to install this plugin (see [installation](#installation) for importanr information), do the action you want to listen for in Sketch manually, and check the logs for the relevant action. In practise, it’s not always that simple, but this plugin will definitely save you a lot of guesswork.

## Installation

- Close Sketch
- Open a Terminal window, and run this: `defaults write ~/Library/Preferences/com.bohemiancoding.sketch3.plist actionWildcardsAllowed -bool YES`. This is a special setting that enable wildcard listeners in Sketch plugins (keep in mind that this will definitely make your Sketch slower, so make sure to disable it with `defaults write ~/Library/Preferences/com.bohemiancoding.sketch3.plist actionWildcardsAllowed -bool NO` when you're done developing your plugin)
- Open Sketch
- Download the plugin and double click it to install

## What is this witchcraft?

The magic happens in `manifest.json`: you’ll see that, instead of a typical action name, we’re using an asterisk, like this:

```json
"handlers" : {
  "actions": {
      "*": "onAction"
  }
},
```

If you have enabled the special setting for wildcard actions (see [installation](#installation) if you haven’t), the `onAction` function will be called for **all** actions in Sketch.

## I have so many questions

Good! Use the Issues in this repo, or send me an email to ale@sketchapp.com, and I’ll be happy to help.