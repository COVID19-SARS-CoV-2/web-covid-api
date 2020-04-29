## Graphql Schema

```graphql

type Query {
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
}


type Continent {
  "Timestamp of the last data updated time"
  updated: Float
  "Total Number of cases"
  cases: Int
  "Total Number of cases for today"
  todayCases: Int
  "Total Number of deaths"
  deaths: Int
  "Total Number of deaths for today"
  todayDeaths: Int
  "Total Number of recovered cases in that continent"
  recovered: Int
  "Total Number of active cases in that continent"
  active: Int
  "Total Number of critical cases in that continent"
  critical: Int
  "Name of the Continent"
  continent: String
  "List of the countries in that Continent"
  countries: [Country]
}

type Country {
  "Timestamp of the last data updated time"
  updated: Float
  "Name of the Country"
  country: String
  "Meta Data oF the Country like Latitude Longitude Flag Country Code"
  countryInfo: CountryMeta
  "Total Number of cases"
  cases: Int
  "Total Number of cases for today"
  todayCases: Int
  "Total Number of deaths"
  deaths: Int
  "Total Number of deaths for today"
  todayDeaths: Int
  "Total Number of recovered cases in that country"
  recovered: Int
  "Total Number of active cases in that country"
  active: Int
  "Total Number of critical cases in that country"
  critical: Int
  "Number of cases taken per million population"
  casesPerOneMillion: Float
  "Number of dealths taken per million population"
  deathsPerOneMillion: Float
  "Total Number of tests taken in that country"
  tests: Int
  "Number of tests taken per million population"
  testsPerOneMillion: Float
  "Name of the Continent"
  continent: String
  "List of the states in that Country"
  states: [State]
  "Get historic cases for the country"
  historical: [Historic]
}

type Historic {
  "Date"
  date: String
  "Number of cases on the day"
  cases: Int
  "Number of deaths on the day"
  deaths: Int
  "Number of recovered on the day"
  recovered: Int
  "Today cases. This data is available only for India"
  todayCases: Int
  "Today recovered. This data is available only for India"
  todayRecovered: Int
  "Today deaths. This data is available only for India"
  todayDeaths: Int
}

type CountryMeta {
  _id: Int
  "Two Alphabet representation of the country name"
  iso2: String
  "Three Alphabet representation of the country name"
  iso3: String
  "Latitude location of the country"
  lat: Float
  "Longtitude location of the country"
  long: Float
  "Image URl of the country's flag"
  flag: String
}

type State {
  "Name of the State"
  state: String,
  "Total Number of cases"
  cases: Int,
  "Total Number of cases for today"
  todayCases: Int,
  "Total Number of deaths"
  deaths: Int,
  "Total Number of deaths for today"
  todayDeaths: Int,
  "Total Number of active cases in this state"
  active: Int,
  "Total Number of tests taken in that state"
  tests: Int,
  "Number of tests taken per million population. This data is only available for USA"
  testsPerOneMillion: Float # USA Only
  "Updated time stamp. This data is available only for India"
  updated: Float # India Only
  "Total number of recovered. This data is available only for India"
  recovered: Int # India Only
  "Today recovered. This data is available only for India"
  todayRecovered: Int # India Only
  "All districts in the state. This data is available only for India"
  districts: [District] # India Only
}

"""
District information for India
"""
type District {
  "District Name"
  district: String
  "Total number of cases"
  cases: Int
  "Today cases"
  todayCases: Int
  "Total number of deaths"
  deaths: Int
  "Today deaths"
  todayDeaths: Int
  "Total number of recovered"
  recovered: Int
  "Today recovered"
  todayRecovered: Int
  "Total active cases"
  active: Int
}

```
