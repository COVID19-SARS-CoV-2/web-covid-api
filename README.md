# Covidstat.info Official

https://covidstat.info

![alt text](https://raw.githubusercontent.com/COVID19-SARS-CoV-2/web-covid-api/master/screenshot.png "Screenshot")

**PS: This repo holds the Official document and doesn't hold the source code, the code cannot be made open source as the UI template has a single user license. Any interested collaborator, please create an issue [here](https://github.com/COVID19-SARS-CoV-2/web/issues/new). I can provide you access**

## API's

Covidstats provides Graphql API's, you can find the detailed schema [here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/blob/master/graphql_schema.md)


### Graphql playground - https://covidstat.info/graphql
### Graphql Endpoint - https://covidstat.info/graphql

## Graphql Queries 
Here are the current possible queries
```graphql
"To get details of the world"
all: Country
"To get all details of cases in all continents"
continents: [Continent]
"To get all details of cases of a particular continent"
continent(name: ID!): Continent
"To get all details of cases in all countries"
countries: [Country]
"To get all details of cases of a particular Country"
country(name: ID!): Country
"To get all details of cases in all States. Currently only USA and India are supported"
states(countryName: ID!): [State]
"To get all details of of a particular state. Currently only USA and India are supported"
state(countryName: ID!, stateName: ID!): State
```

**Historical data soon to be available**

**PS: State information is currently available only for India and USA**

We are constantly expanding our data. If you need any customized graphql query [create an issue here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/issues/new) we are happy to help 

You can also contribute by yourself. Please [create an issue here](https://github.com/COVID19-SARS-CoV-2/web/issues/new) we will give access to the source code 
