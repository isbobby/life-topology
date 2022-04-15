## [[Ruby]] as Datadog Client
[**Datadog Documentation**](https://docs.datadoghq.com/api/latest/)

[**Ruby Datadog API**](https://github.com/DataDog/dogapi-rb)

### Installation
```
$  sudo gem install dogapi
# on ubuntu e.g.
$ sudo apt-get install ruby-dev
```

**!** For Mac OS, installation via gem may not succeed due to a `'ruby/config.h' file not found` error. This [post](https://stackoverflow.com/questions/53135863/macos-mojave-ruby-config-h-file-not-found) provides a work around by making a symbolic link manually.

## Query Metrics
### Initialize `dogapi`
`Dogapi::client` requires `api_key` and `application_key`. These keys can be found on the [Datadog site]()
```
require 'rubygems'
require 'dogapi'

api_key = "abcd123"
application_key = "brec1252"

dog = Dogapi::Client.new(api_key, application_key)
```


## Query APM Latency

## Bonus - Populate Google sheet
Metrics queried from Datadog can be used to populate sheets for easy viewing. This requires the support of Google API Client.

### Setting Up Google API Client in [[Ruby]] (For Sheets)
1. **Installation**
```
$ gem install google-api-client 
```

2. **Google Credentials**
When your application requests private data, the request must be authorized by an authenticated user who has access to that data.

Every request your application sends to the Google Sheets API needs to identify your application to Google. There are two ways to identify your application: using an [OAuth 2.0 token](https://developers.google.com/sheets/api/guides/authorizing#AboutAuthorization) (which also authorizes the request) and/or using the application's [API key](https://developers.google.com/sheets/api/guides/authorizing#APIKey). Here's how to determine which of those options to use:

-   If the request requires authorization (such as a request for an individual's private data), then the application must provide an OAuth 2.0 token with the request. The application may also provide the API key, but it doesn't have to.
-   
-   If the request doesn't require authorization (such as a request for public data), then the application must provide either the API key or an OAuth 2.0 token, or both—whatever option is most convenient for you.

3. **How Google Sheets are Indexed**

4. **Inserting rows into sheets**


steps
1. Create service account (if not already exists)
2. Enable both drive and sheet API
3. Create a new API key 
4. Download and keep it safe (the JSON file below)
5. Export the following environment variables
6. To write to a sheet, get the sheet ID
7. This sheet ID is contained within each JSON file
8. `service.batch_udpate_spreadsheet(spreadsheet_id, body, {})` writes a new row to the specified sheet
9. Update the spreadsheet ID and sheet ID accordingly

**rake file steps**
1. 

```
def insert_new_row(spreadsheet_id, sheet_id, row_number)
    requests = [{
      insert_dimension: {
        range: {
          sheet_id: sheet_id,
          dimension: "ROWS",
          start_index: row_number - 1,
          end_index: row_number
        },
        inherit_from_before: false
      }
    }]
    body = {requests: requests}
    service.batch_update_spreadsheet(spreadsheet_id, body, {})
  end
```

json file
```
{

"type": "service_account",

"project_id": "sheet-service-project",

"private_key_id": "89533382e2ee19c5453f782ac2ee793c990c0bdf",

"private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQDA9ugelbvUnPwf\nIlW6ELUFQdkLLouWumNa2rdqSYpeg6dZMSOnjFo/7BUlgAIWWwDAZdv1gOP4ukQU\nqSj27cP9WnUZEWxapGKxCCY+hfbQLTaNxex4YTMUISiRwwQIIaD4L7nnfMus0CZz\nDwW1cKa3b84ng6ytKNgqVfW9DfTx0yZgynF7GuiZSlsvqcyFZZoo5UVWmL8VF3p6\ndljF5bVl8F0zR6HLlbC5MBWy9A13Wg4UKnP6DfOsqKWKinpo9CPpmqZqJGWfIkTq\nfxZpxlz2RDsr6iPFaPjdu+r29Pqp2ngK3aEROSlZgJVElo0FpEFS6LBDTsD3+hLu\nN7v4KZs7AgMBAAECggEABydADJ41Y9jb+dV+gxLKeyLpRmJX12Maesw/32dRg1Zz\nFjndngD0eYkpcYXwzd5axUchY9T+3oIdMvzgYWMIEHTRgXflYejVJcXtEQVLVIVQ\nj+nl7cKAr77Y76pglGKWwoyWYi/8pu/idQJ6DjNaYtN4u3tEo/ivJsagAP2q9mny\nZjmwKnjXXJ+3ZpikxBhxo/ZpkrOXE8Bx9lrZbHOUYhtBv5KHsnli3JRmyvL1dt5A\nBb2czMCO5romBcLkfTbcfUSK+cMr4L4Hz+1+LuCrceBpkvuAPXVG9+K4xqO1J/nZ\npZhK5OSYBIwIlnjGQEcYuI2J47hKR1bB1RzH4kkCwQKBgQDzvi15nGW/Vc2uAAo8\nMroFEVvuHwk8x6/TrkAC99N7Xyo36dYdh2xNbf7mFe49kx2jT7/mQCqDn38iQrmg\nqFMjUT+DgSMqkAbcCfeVaeoS+WPPQVRQY+elyuRxk00rRj6c5ScyXApVuqjBBtLJ\ndogT7vrBsknqTo8Nff7P4DghQQKBgQDKqwid3ac3i42IiVepiMGiAoJh5nXE3HG+\nofpm8uXvdN9YQIKcctUbpQvYYawLcdUqH3FmA+1GFWA6HAr9QFrbLLc0lJY2EB4k\nwkFrkeu+oQ95oC9hlYERnum9Nd+SunynNHiUnzbYIvk3th0K8VUT+uY+8AuHnp0b\neYkpuphhewKBgQCP80RGK0DIFHOpjKp+zPKhpZPmePvqooBMAwAZAKYsmZKEfRyQ\nSfeDby/4UQFn6ie52JKb+E9jduINqNyabm7TT9uz3aOYMoFqmJRY8LlmRVVWBN43\nsBkSCFaMYRNVOGIoJQnWKxeLc/bQMShyBQfuxdfgZ1xR/d1seXnw6RodQQKBgQCT\n8QX5NzQ5d8V5RciYGRxAB1Tl4jVV3xWo8tS3EdiHU+k1ouG1Ep49790Vtza/o/jX\nJtzAe11ZK4Fy6cWb2L55/8o8t7pu/JUEgEkBHSPZo/iH8EamFVyCYF5/oDP0B+22\noLbkxtRiMiV6ZZYNxt00GJK6nr/L4B0PUUivDWbuwQKBgEciqHBrbVe0esTTH2TT\nLzBN6tvhRjYk5f+JD20OugXgwgAwH0uczjPnEFYaVZ4cXWcQeJgnV6HXFr2+8sG1\nu0negZkKO8D5gCbQWiu4fdLdkt9PcgbuongyQ75peEdHiDzKVZUwTGbREaIOy4xc\n0+Mq/6A+zOe2hRHVDpFEhZ0M\n-----END PRIVATE KEY-----\n",

"client_email": "google-sheet-worker@sheet-service-project.iam.gserviceaccount.com",

"client_id": "114375104988438633568",

"auth_uri": "https://accounts.google.com/o/oauth2/auth",

"token_uri": "https://oauth2.googleapis.com/token",

"auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",

"client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/google-sheet-worker%40sheet-service-project.iam.gserviceaccount.com"

}
```

- [ ] fill up the remaining query metrics
- [ ] make a spreadsheet explaining the metrics and their queries
- [ ] document next step - basically just change the environment variables
- [ ] refactor code
- [ ] populate the missing metrics for the past few weeks
- [ ] check for nil class when metric is missing, return 0