 # Tecnical test Covela

## Intro
Insurances companies classify other companies according to their industry. Data about those industries may change widely from one day to another. This is why we need to be able to submit a csv file in case we have big changes to submit. Moreover, in order to improve the product in the future, we want track why the api is used for.

an industry uses to have the following format:
```json
{
  "id": "11",
  "name": "Agricultura",
  "children": [
    {
      "id": "111",
      "name": "Siembra de soya"
    },
    {
       "id": "1111",
       "name": "Siembra de mais"
    }
  ]
}
```

In this test you'll have to build an API that enable the following:

#### As a user, when I login through a name/description, I want to be able to submit a csv file, so that I can update industries in DB
#### As a user, I want to be able to see data from an industry in db, so that I may have info about an industry

In order to do that, you'll have to follow the following specifications:

## Language
* Node

## Endpoints
### POST /apps/register
payload:
- name: String
- description: String

response:
- token: String

NOTE: this is not a tipical email/password login : we want to test your problem solving skills when you have to manage something a bit weird. We need this endpoint to track how users use the product.

### POST /industries/upload 
authorization required

formdata:
- file.csv

NOTE: This is where the magic happens: converting a csv tile to industries. You are free to format the csv file. Keep in mind that an industry may have other industries as children industries.

### GET /industries
authorization required 

response:
```json
data: [
  {
    "id": "11",
    "name": "Agricultura",
    "children": [
      {
        "id": "111",
        "name": "Siembra de soya"
      },
      {
        "id": "1111",
        "name": "Siembra de soya"
      }
    ]
  },
  {
    "id": "12",
    "name": "Comercio de ropa",
    "children": [
      {
        "id": "121",
        "name": "venta de camiseta"
      },
      {
        "id": "1121",
        "name": "venta de pantalon"
      }
    ]
  },
  {
    "id": "111",
    "name": "Siembra de soya"
  },
  {
    "id": "1111",
    "name": "Siembra de soya"
  },
  {
    "id": "121",
    "name": "venta de camiseta"
  },
  {
    "id": "1121",
    "name": "venta de pantalon"
  }
]
```
### GET /industries/:industryId 
authorization required
response:
```json 
{
"data": {
  "id": "11",
  "name": "Agricultura", 
  "children": [
    {
      "id": "111",
      "name": "Siembra de soya"
    },
    {
      "id": "1111",
      "name": "Siembra de soya"
    },
  ] 
}
```
## Building the client
Once you've build the api, build a client with Vue or React that let a user interact with the api. 
Through this client, we want to see how you perform with auth management within a SPA.

## How are we going to judge you?

In Covela, we love being agile, so according to the agile manifesto: 

### We value individuals and interactions over processes and tools: 
- if you have any doubt, you should contact us in order that we can help you.
- As we are individuals and we don't know you (for the moment) and your mindset, you should add a readme.

### We value working software over comprehensive documentation
- we can login through a name/description login, we can submit a csv that'll update/create industries, we are able to read the industries (it means that the software is complying with what we've asked for)
- you have deploy the code in production. Heroku + Firebase are free. GCP offers 300USD if you create an account, which make it free too.

### We value Customer collaboration over contract negotiation
- this doesnt really apply now. In general, this apply when you are building a product for someone else (i.e: web agency)

### We value Responding to change over following a plan

- this doesnt really apply either. Just keep in mind that in Covela, we may reshape the plan frequently according to the priority of the moment.


#### According to your experience, we'll also value: coding style, git skills, e2e tests, unit tests, code complexity compared to features, good practices/knowledge in React/Vue, ui design, general ux, speed
