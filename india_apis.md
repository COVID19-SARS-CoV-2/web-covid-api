## India API's
All India related data comes from https://github.com/covid19india/api

Covidstats provides Graphql API's, you can find the detailed schema [here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/blob/master/graphql_schema.md)

### Graphql playground - https://covidstat.info/graphql
### Graphql Endpoint - https://covidstat.info/graphql

## Graphql Queries 
Useful graphql queries for India. [Worldwide queries can be found here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/blob/master/README.md#apis)
```graphql
country(name: ID!): Country # Pass "India" as the country name
state(countryName: ID!, stateName: ID!): State # Pass "India" as the country name and the state name you want
```
### Few examples
Open Graphql playground https://covidstat.info/graphql
#### 1. To get no of cases for all states
```graphql
query {
  country(name: "India") {
    states {
      state
      cases
    }
  }
}
```
#### 2. To get cases, recovered and deaths of all states 
```graphql
query {
  country(name: "India") {
    states {
      state
      cases
      deaths
      recovered
    }
  }
}
```
#### 2. To get cases, recovered, deaths, tests and today data of all states 
```graphql
query {
  country(name: "India") {
    states {
      state
      cases
      deaths
      recovered
      tests
      todayCases
      todayDeaths
      todayRecovered
    }
  }
}
```
#### 3. To get district information of all states 
```graphql
query {
  country(name: "India") {
    states {
      state
      districts {
        district
        cases
        todayCases
        deaths
        todayDeaths
        recovered
        todayRecovered
        active
      }
    }
  }
}
```
#### 4. Get particular state information along with districts 
```graphql
query {
  state(countryName: "India", stateName: "Tamil Nadu") {
    state
    cases
    deaths
    districts {
      district
      cases
      deaths
    }
  }
}
```
#### 5. Get historic data 
```graphql
query {
  country(name: "India") {
    historical {
      date
      cases
      deaths
      recovered
      todayCases
      todayRecovered
      todayDeaths
    }
  }
}
```
#### 6. Complete dump of all data 
```graphql
query {
  country(name: "india") {
    country
    updated
    countryInfo {
      _id
      iso2
      iso3
      lat
      long
      flag
    }
    cases
    todayCases
    deaths
    todayDeaths
    recovered
    tests
    historical {
      date
      cases
      deaths
      recovered
    }
    states {
      state
      cases
      todayCases
      todayDeaths
      tests
      active
      updated
      districts {
        district
        cases
        todayCases
        deaths
        todayDeaths
        recovered
        todayRecovered
        active
      }
    }
    historical {
      date
      cases
      deaths
      recovered
    }
  }
}
```

_Historic data for state is not available at the moment. If you want that data [please create an issue here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/issues/new) we will do our best to process it_

_Raw & resource data is also not present on the system. [Create an issue here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/issues/new) if you want that in graphql_

### Notes
1. **All the data above are processed from [covid19india apis](https://github.com/covid19india/api#json)**
2. **Data is refreshed every 3 mins**
