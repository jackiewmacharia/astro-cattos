
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
