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

## Can be used with any REST api framework

Graphql is also supported in any rest client

1. axios - NodeJS and Browser - [Example](https://medium.com/@stubailo/how-to-call-a-graphql-server-with-axios-337a94ad6cf9)
2. Android - Apollo client - [Example](https://github.com/apollographql/apollo-android)
3. iOS - Apollo client - [Example](https://www.apollographql.com/docs/ios/)
4. [Other supported languages](https://www.apollographql.com/docs/)

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

#### 5. Get historic data for India

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

#### 6. Get historic data for State

```graphql
# Get historical data for all state
query {
  country(name: "India") {
    states {
      state
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
}

or

# Get historical data for a particular state
query {
  state(countryName: "India", stateName: "Tamil Nadu") {
    state
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

#### 7. Get historic data for district

```graphql
# Get historical for all districts in all states
query {
  country(name: "India") {
    states {
      state
      districts {
        district
        historical {
          date
          cases
          deaths
          recovered
        }
      }
    }
  }
}

or

# Get historical for all districts in a particular state
query {
  state(countryName: "India", stateName: "Tamil Nadu") {
    state
    districts {
      district
      historical {
        date
        cases
        deaths
        recovered
      }
    }
  }
}
```

#### 8. Complete dump of all data

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
        historical {
          date
          cases
          deaths
          recovered
        }
      }
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
    historical {
      date
      cases
      deaths
      recovered
    }
  }
}
```

### Historical filter

Filters can be applied on any historical data with these parameters

1. `count: Int`
2. `skip: Int`
3. `reverse: Boolean`

#### Examples

#### 1. Get last 5 days cases for a state

```graphql
query {
  state(countryName: "India", stateName: "Tamil Nadu") {
    state
    historical(reverse: true, count: 5) {
      date
      cases
    }
  }
}
```

#### 2. Get previous week data for all districst in a state

```graphql
query {
  state(countryName: "India", stateName: "Tamil Nadu") {
    state
    districts {
      district
      historical(count: 7, skip: 7, reverse: true) {
        date
        cases
      }
    }
  }
}
```

_Raw & resource data is also not present on the system. [Create an issue here](https://github.com/COVID19-SARS-CoV-2/web-covid-api/issues/new) if you want that in graphql_

**PS: Variable names, will be different from what you see in covid19india, all the variable names will follow the [NovelCOVIDAPI](https://github.com/NovelCOVID/API) standards**

### Notes

1. **All the data above are processed from [covid19india apis](https://github.com/covid19india/api#json)**
2. **Data is refreshed every 3 mins**
