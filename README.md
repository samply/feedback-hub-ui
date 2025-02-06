# Feedback hub UI
This is the UI for the feedback hub part of the metadata feedback system. It
provides a fontend that allows researchers to associate metadata (e.g. the DOIs of relevant publications) with
samples held at biobanks that have installed the feedback agent.

Implemented with with Vue 3 in Vite.

TODO: VITE_BACKEND_URI is set in .env at build time. This needs to be settable at execution time, so that it can be passed as an environment variable to Docker.

## Building for production
If you want to run the feedback hub UI centrally together with the [feedback hub backend](https://github.com/samply/feedback-hub),
you will need to clone the repository and build the container:
``` code
git clone https://github.com/samply/feedback-hub-ui.git
cd feedback-hub-ui
docker build -t samply/feedback-hub-ui .
```

## Running the UI
If you just want to test the feeback hub UI locally on your computer, follow these steps.

### Docker
Build as shown above, and then:
``` code
docker run -p 8095:8095 samply/feedback-agent-ui
```
This will build the app and make it available on ```http://localhost:8095``` in a locally
running browser.

### Build and test with npm

```sh
npm install
npm run dev
```
This will build the app and make it available on ```http://localhost:8095``` in a locally
running browser.

## Using the UI
When the UI first opens, you will see two data entry fields plus a button.

To use first enter a request ID into the first field. This ID is an arbitrary string, but it should be unique. It serves to identify the piece of metadata that you wish to append to specimens.

In the seond field you should enter the metadata string that should be added to specimens. E.g. a DOI.

Then click the "Submit" button.

If a feedback hub backend is present and there is at least one Bridgehead with an activated feedback agent, you will
see an acknowledgement of your metadata submission after a few minutes. This tells you that
the metadata has been passed on to all known activated Bridgeheads.

