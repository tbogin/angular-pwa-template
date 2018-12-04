# Angular PWA example

## Running the app
Service workers do not work with `ng serve`
To run application, run `http-server -p 8080 -c-1 dist/<project-name>`

## Understanding manifest.json
`name` - title
`short_name` - abbreviated title if `name` is too long
`start_url` - app's landing page
`theme_color` - color that browser UI assumes on the site
`background_color` - for which app icon is displayed
`display` - specify whether browser UI should be hidden when users visit the site

## Adding PWA package to an Angular app
`ng add @angular/pwa@v6-lts --project project-name`

`SwUpdate` imported into app-component.ts, used to subscribe to updates

`ngsw-config.json` is where you cache info on api endpoint for pwa to work offline

"cacheConfig": {
    "strategy": "freshness",
    "maxSize": 20,
    "maxAge": "1h",
    "timeout": "5s"
}
In `ngsw-config`, checks api endpoint for updates before falling back on existing service worker cache if user is offline
To check cache before network, use `"performance"` instead of `"freshness"`
`maxSize` is max number of endpoint responses that will be cached by service worker
`timeout` used in conjunction with strategy freshness
`maxAge` - how long a cached response is valid

https://angular.io/guide/service-worker-getting-started