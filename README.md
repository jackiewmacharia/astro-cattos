### Repro code repo

Minimal repro for Edge Functions manifest route patterns validation error

Prerequisites:
At least netlify-cli@10.17.8 `npm install netlify-cli@10.17.8 -g`

Repro Steps:

`npm i && netlify build`


Error

```sh
────────────────────────────────────────────────────────────────
  Internal error during "Edge Functions bundling"
────────────────────────────────────────────────────────────────

  Error message
  Error: [
    {
      "instancePath": "/routes/2/pattern",
      "schemaPath": "#/properties/routes/items/properties/pattern/errorMessage",
      "keyword": "errorMessage",
      "params": {
        "errors": [
          {
            "instancePath": "/routes/2/pattern",
            "schemaPath": "#/properties/routes/items/properties/pattern/format",
            "keyword": "format",
            "params": {
              "format": "regexPattern"
            },
            "message": "must match format \"regexPattern\"",
            "emUsed": true
          }
        ]
      },
      "message": "must match format /^\\^.*\\$$/"
    }
  ]

```


### Testing fix instructions:
* Clone my astro fork branch [fix/netlify-edge-functions-route-pattern-serialization](https://github.com/jackiewmacharia/astro/tree/fix/netlify-edge-functions-route-pattern-serialization) and set it up as per README instructions
* Clone this repo and change these two packages to use the local astro instance in this way:

```json
    "astro": "/Users/jackie/oss/astro/packages/astro",
    "@astrojs/netlify": "/Users/jackie/oss/astro/packages/integrations/netlify"
```
* In `astro-cattos` run `npm i && netlify build` Netlify CLI needs to be at least version 10.17.8. Build should complete without errors.
