Git Conflict Resolver
===========================

A Sublime Text plugin to help you solve this nasty merge conflicts.

Commands
---------

Git Conflict Resolver ships with five commands: `Find Next Conflict`, `Keep Head`, `Keep Current`, `Keep Common Ancestor`, `Swap Head and Current` and `Show Conflict Files`.

While most of them are pretty self explaining, the `Keep Common Ancestor` could need some elaboration:
This command is especially useful for the diff3 conflict type of Git. If you have no idea what I'm talking about then
[check it out](http://git-scm.com/docs/git-merge) it's great! (Just search for diff3 on the page)

Some clarification:
The first block always represents `head` while the last block is always `current`.

Configuration
-------------

To configure the plugin you can use a user-settings file in your user folder. You can easily access this file over `Preferences` -> `Git Conflict Resolver` -> `Settings - User`.

For information on which settings are available take a look at the commented default-settings file:

```js
{
    // The git path
    // by default the plugin assumes that git is in your path
    "git_path": "git",

    // Enable or disable the live matching of conflict areas
    // By default the plugin matches live
    "live_matching": true,

    // The color of the highlighting is called "scope" in Sublime Text,
    // to change this color you can choose a different scope.
    // This customization isn't easy, since you have to define your own
    // scope in your theme file.
    "matching_scope": "invalid",

    // This option enables the filling the conflict area with a color
    // By default the area will just be outlined
    "fill_conflict_area": false,

    // This option enables the outline of the conflict area
    // By default the area will just be outlined
    // In Sublime Text 2 the area will only be outlined if "fill_conflict_area" is false
    "outline_conflict_area": true,

    // This options enable the gutter marks for the different conflict groups
    "head_gutter": true,
    "current_gutter": true,
    "ancestor_gutter": true,

    // This option changes the display of the "Show Conflict Files" functionality"
    // true: Show only the filesnames ("src/main.js" becomes "main.js")
    // false: Show relative path (from the root of the repository)
    // By default Git Conflict Resolver only shows the filename
    "show_only_filename": true
}
```

Shortcuts
---------

There are no default shortcuts, to add them open your user keybindings file and add a keybinding like the following:

      { "keys": ["ctrl+alt+f"], "command": "find_next_conflict" },
      { "keys": ["ctrl+alt+a"], "command": "keep", "args": { "keep": "ancestor" } },
      { "keys": ["ctrl+alt+b"], "command": "keep", "args": { "keep": "both" } },
      { "keys": ["ctrl+alt+o"], "command": "keep", "args": { "keep": "current" } },
      { "keys": ["ctrl+alt+t"], "command": "keep", "args": { "keep": "head" } },
      { "keys": ["ctrl+alt+s"], "command": "keep", "args": { "keep": "swap" } },
      { "keys": ["ctrl+alt+c"], "command": "list_conflict_files" }


Tests
---------

Tests written for new "keep both" feature & "swap" feature under tests folder

Run the tests in main directory

`py -3 -m test.main`