# TIFY

The fastest IIIF document viewer. [Check out the demo.](https://subugoe.github.io/tify/demo.html?manifestUrl=https://gdzdev.sub.uni-goettingen.de/iiif/presentation/PPN857449303/manifest)

## Embedding TIFY

To embed TIFY into your site:
1. Copy the contents of the `dist/` directory to your server.
2. Add an HTML element serving as the container
3. Load `tify.js`.

The container element should have the following CSS applied:
- either `position: relative` or `position: absolute`
- `height` and `width`

The required HTML code looks something like this:

``` html
<div id="tify"></div>
<script src="tify.js"></script>
```

The only required parameter `manifestUrl` is a URL pointing to the manifest. It can be set either as a query parameter or with the `tifyOptions` object, whereby the latter takes precedence.

### Options
- `container` (default: `#tify`): The HTML element TIFY is loaded into.
- `language` (default: `en`): The interface language. Currently, only English and German (`de`) are available.
- `manifestUrl`: A URL pointing to the IIIF manifest. If this option is not set, the URL has to be provided via a query parameter of the same name.
- `stylesheetUrl`: Provide your own stylesheet, replacing TIFY's default styles. Use `null` to disable loading any styles, e.g. if your site's stylesheet already includes styles for TIFY.
- `title` (default: `TIFY`): By default, TIFY replaces the window title with the document title as defined by the manifest, appended by `TIFY`. Set this to any string, or `null` to disable title modification.

### Example

Below an example with all available options set.

``` html
<div id="viewer"></div>
<script>
	tifyOptions = {
		container: '#viewer',
		language: 'de',
		manifestUrl: 'https://example.com/iiif/manifest.json',
		stylesheetUrl: '../styles/my-very-own-tify-styles.css',
		title: null,
	}
</script>
<script src="tify.js"></script>
```

## Build Setup

Install dependencies:

``` bash
npm install
```

Run in development mode with hot reload on `localhost:8080`:

``` bash
npm run dev
```

In development mode, the manifest URL must be provided via query parameter, e.g. `http://localhost:8080/?manifestUrl=http://gdzdev.sub.uni-goettingen.de/api/PPN616082037/manifest`.

Build for production with minification:

``` bash
npm run build
```

The production build will be stored in `dist`, just copy the contents of this directory to your server.

## Running Tests

While Karma and all requires plugins are part of the dev dependencies, CodeceptJS, which is used for end-to-end tests, is not. If needed, install CodeceptJS with `npm install -g codeceptjs`.

Run tests:

``` bash
# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```
