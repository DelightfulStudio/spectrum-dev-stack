# spectrum-dev-stack

A simple [Docker](https://store.docker.com/search?type=edition&offering=community) stack to jump-start [Spectrum](https://github.com/withspectrum/spectrum)'s local dev env setup.

This stack eliminates the need to manually install Spectrum's background services (**RethinkDB** and **Redis**) on your local machine, or start them separately. Please note that this stack is not intended for deployment, and does not provide Node.js environment for Spectrum itself, other people are [working](https://github.com/withspectrum/spectrum/issues/2790) on it.

### First time setup

Follow the original Spectrum [instructions](https://github.com/withspectrum/spectrum#first-time-setup), but skip the steps for **RethinkDB** and **Redis** in the Installation section. Once you have `yarn` installed, clone this repo, make sure your [Docker app](https://store.docker.com/search?type=edition&offering=community) is running, `cd spectrum-dev-stack` and run `yarn start`. It's going to take a couple of minutes for the `yarn` script to set things up for the first time.

Once `yarn start` has completed successfully, **RethinkDB** and **Redis** will be up and running (each inside of a corresponding docker container), and you won't need to start them manually, so you can skip those steps in the rest of the [original instructions](https://github.com/withspectrum/spectrum#installation).

### Restarting background services

The set up **RethinkDB** and **Redis** containers will remain running until you explicitly shut them down, restart your machine, or restart your Docker app.

To start them back up again, simply `cd` to your `spectrum-dev-stack` directory and run `yarn start`. 

### List of commands

The full list of available commands for managing the services:

* `yarn start` — creates (if needed) and starts the services' containers; the containers will run until stopped or Docker is restarted
* `yarn stop` — stops the containers
* `yarn down` — deletes the services' containers; persistent volumes used by the containers will stay around until manually deleted with `docker volume rm spectrum_rethinkdb spectrum_redis` or `docker volume prune` commands
