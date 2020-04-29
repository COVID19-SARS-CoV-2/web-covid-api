## India API's
All India related data comes from https://github.com/covid19india/api

Covidstats provides Graphql API's, you can find the detailed schema [here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/blob/master/graphql_schema.md)

### Graphql playground - https://covidstat.info/graphql
### Graphql Endpoint - https://covidstat.info/graphql

## Graphql Queries 
Here are the current possible queries
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

### FAQ's
1. asdfasdf
- asdfasdf
2. asdf
- asdfsd
