# ADR logger
This is a Google Docs add-on that will help you log stuff to github. The use case is for [ADR logging](https://github.com/joelparkerhenderson/architecture_decision_record).

The UI is developed in [Svelte](https://svelte.dev/) because it is easy to use for building components.

## Setup

1. Ensure you have [node & npm](https://github.com/nvm-sh/nvm#install--update-script) installed
2. clone this repo
3. `npm install`
4. `cd sidebar/ && npm install`

Then go back to root `cd ..` and proceed with the following steps.

## Connect to Google Apps Script

1. Log in and authenticate with your Google account:
   ```
   npm run clasp:login
   ```
1. Create a new _standalone_ project:
   ```
   npm run clasp:create
   ```
1. Deploy the project:
   ```
   npm run deploy
   ```
1. Open the project:
   ```
   npm run clasp:open
   ```

## Test the add-on

Once you followed the steps above and have the Apps Script project open, the following steps explain how to test the add-on:

1. Click **Run**, then **Test as add-on...**
1. Click **Select Doc** and choose a document you want to use for testing.
1. Click **Save**
1. In the *Execute Saved Test" section that appeared at the top, select your document and click **Test**.
1. With the document now open, navigate to **Add-ons** menu

This opens the Svelte sidebar.

## Sidebar development

Navigate to the `sidebar` folder and develop & test the application as you would any regular Svelte application, i.e. `npm run dev`.

## Demo

Watch the [demo](./demo.mov) of how this add on works. The demo creates ADR into [this repo](https://github.com/geekyme/sample-adr)
