# Focalboard

Like what you see? :eyes: Give us a GitHub Star! :star:

[![Focalboard](website/site/static/img/hero.jpg)](https://www.focalboard.com)

[Focalboard](https://www.focalboard.com) is an open source, self-hosted alternative to Trello, Notion, and Asana. 

It helps define, organize, track and manage work across individuals and teams. Focalboard comes in two editions:

* **Focalboard Personal Desktop**: A stand-alone desktop app for your todos and personal projects
* **Focalboard Personal Server**: A self-hosted server for your team to collaborate

The same server binary powers both editions.

## Building the server

Please refer to the [Developer's Tips & Tricks](https://www.focalboard.com/contribute/getting-started/dev-tips/) for more detailed steps. Here's a summary:

First, install basic dependencies:
* Go 1.15+
* Node 10+ and npm
* Mingw64 on Windows

```
make prebuild
make
```

## Running and testing the server

To start the server, run `./bin/focalboard-server`

Server settings are in config.json.

Open a browser to [http://localhost:8000](http://localhost:8000) to start.

## Building and running standalone desktop apps

You can build standalone apps that package the server to run locally against SQLite:

* Mac:
    * `make mac-app`
    * run `mac/dist/Focalboard.app`
    * *Requires: macOS Catalina (10.15)+, Xcode 12+.*
* Linux:
    * Install webgtk dependencies
        * `sudo apt-get install libgtk-3-dev`
        * `sudo apt-get install libwebkit2gtk-4.0-dev`
    * `make linux-app`
    * run `linux/dist/focalboard-app`
    * *Tested with: Ubuntu 18.04*
* Windows:
    * Open a git-bash prompt
    * Install win-node-env `npm install -g win-node-env`
    * `make win-wpf-app`
    * run `cd win-wpf/msix && focalboard.exe`
    * *Requires: Windows 10*

Cross-compilation currently isn't fully supported, so please build on the appropriate platform. Refer to the GitHub Actions workflows (build-mac.yml, build-win.yml, build-ubuntu.yml) for the detailed list of steps on each platform.

## Unit tests

Before checking-in commits, run: `make ci`, which is simlar to the ci.yml workflow and includes:
* Server unit tests: `make server-test`
* Webapp eslint: `cd webapp; npm run check`
* Webapp unit tests: `cd webapp; npm run test`
* Webapp UI tests: `cd webapp; npm run cypress:ci`

## Stay informed on progress

* **Changelog**: See [CHANGELOG.md](CHANGELOG.md) for the latest updates
* **Chat**: Join the [Focalboard community channel](https://community.mattermost.com/core/channels/focalboard)

## Contributing

Contribute code, bug reports, and ideas to the future of the Focalboard project. We welcome your input! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details on how to get involved.
