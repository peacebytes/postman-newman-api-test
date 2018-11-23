# postman-newman-api-test
An example how to use Postman to verify web services.


# Limitation
- Postman share link to collection is not supported v2.* so newman 4 couldn't run directly from share link.
https://github.com/postmanlabs/newman/issues/1763

# Jenkins 
Execute shell
```
newman run switbe-demo.postman_collection.json -e staging.postman_environment.json -r html --reporter-html-export newman_switbe_report.html
```
Use Jenkins plugin `Publish HTML reports` to display HTML report.
Set `Index page(s)` : `newman_switbe_report.htm`
