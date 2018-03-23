---
title: Commands
---

A basic command looks like the following in TypeScript:

```js
import Command from '@oclif/command'

export class MyCommand extends Command {
  static description = 'description of this example command'

  async run() {
    console.log('running my command')
  }
}
```

The only part that is required is the run function. Accept user input with [arguments](args.md) and [flags](flags.md).

In JavaScript:

```js
const {Command} = require('@oclif/command')

class MyCommand extends Command {
  async run() {
    console.log('running my command')
  }
}

MyCommand.description = 'description of this example command'

module.exports = MyCommand
```

Note that the following examples will be in TypeScript. As JavaScript does not yet have static class properties, you will have to add them to the class after it is declared like we did with the description above.

### Other Command Options

[See the base class to get an idea of what methods can be called on a command](https://github.com/oclif/command/blob/master/src/command.ts).

```js
import Command, {flags} from '@oclif/command'

export class MyCommand extends Command {
  static description = `
description of my command
can be multiline
`

  // hide the command from help
  static hidden = false

  // custom usage string for help
  // this overrides the default usage
  static usage = 'mycommand --myflag'

  // examples to add to help
  // each can be multiline
  static examples = [
    '$ mycommand --force',
    '$ mycommand --help',
  ]

  // this makes the parser not fail when it receives invalid arguments
  // defaults to true
  // set it to false if you need to accept variable arguments
  static strict = false

  async run() {
    // show a warning
    this.warn('uh oh!')
    // exit with an error message
    this.error('uh oh!!!')
    // exit with status code
    this.exit(1)
  }
}
```