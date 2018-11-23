# postman-newman-api-test
An example how to use Postman to verify web services with Jenkins integration.

# How does it work:
- Using Postman (stand-alone version; don't use the Chrome add-on one) to import the Collection file `switbe-demo.postman_collection.json`. Import the environment settings file too `staging.postman_environment.json`
- Running test on local is simple. See https://www.npmjs.com/package/newman
Example
```
newman run switbe-demo.postman_collection.json -e staging.postman_environment.json -r html --reporter-html-export newman_switbe_report.html
```

# Report
HTML report is `newman_switbe_report.html`

# Limitation
- Postman share link to collection is not supported v2.* so newman 4 couldn't run directly from share link.
https://github.com/postmanlabs/newman/issues/1763

# Jenkins 
- Exporting Collection & Environment as json files and pushing them on a source control server.
- Jenkins pull those files to its workspace and execute test as:
```
newman run switbe-demo.postman_collection.json -e staging.postman_environment.json -r html --reporter-html-export newman_switbe_report.html
```
- Use Jenkins plugin `Publish HTML reports` to display HTML report. Set `Index page(s)` : `newman_switbe_report.html`
