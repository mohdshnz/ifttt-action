

# :rocket: ifttt-action

<p>
    <img alt="units-test status" src="https://github.com/actions/javascript-action/workflows/units-test/badge.svg">
    <img alt="workflows status" src="https://github.com/awais786327/ifttt-action/workflows/CI%20Setup%20for%20IFTTT%20Webhook/badge.svg">
</p>

GitHub action that pull Github Issues into Trello by simply trigger an IFTTT webhook event. This makes it easy to manage and sync your Github work with a Trello-based workflow. You can customize the board and list name or you can create you own ifttt applet [here](https://ifttt.com/create)

![demo](demo.gif)

## Getting Started

Install the dependencies  
```bash
$ npm install
```

## Change the Code

Most toolkit and CI/CD operations involve async operations so the action is run in an async function.

```javascript
const core = require('@actions/core');
...

async function run() {
  try { 
      ...
  } 
  catch (error) {
    core.setFailed(error.message);
  }
}

run()
```

See the [toolkit documentation](https://github.com/actions/toolkit/blob/master/README.md#packages) for the various packages.

## Package for distribution

GitHub Actions will run the entry point from the action.yml. Packaging assembles the code into one file that can be checked in to Git, enabling fast and reliable execution and preventing the need to check in node_modules.

Actions are run from GitHub repos.  Packaging the action will create a packaged action in the dist folder.

Run package

```bash
npm run package
```

Since the packaged index.js is run from the dist folder.

```bash
git add dist
```

## Create a release branch

Users shouldn't consume the action from master since that would be latest code and actions can break compatibility between major versions.

Checkin to the v1 release branch

```bash
$ git checkout -b v1
$ git commit -a -m "v1 release"
```

Just push your action 

```bash
$ git push origin v1
```

All set! Your action is now published! :rocket: 

## Usage

Update the action.yml with your ifttt event and key for your action. You can now consume the action by referencing the v1 branch

See [action.yml](https://github.com/awais786327/ifttt-action/blob/master/action.yml)

```yaml
steps:
  - uses: awais786327/ifttt-action@v1
    with:
      event: your-webhook-event
      key: your-webhook-secret-key
```

## LICENSE 📋
[Licensed under the MIT License (the "License")](./LICENSE);
