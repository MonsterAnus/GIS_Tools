<h1>Get County and States FIPS Code and Name</h1>
<h2>The code samples are set up as user-defined functions</h2>
<h3>The original code this was adapted from can be found <a href = "https://gist.github.com/cjwinchester/a8ff5dee9c07d161bdf4" target="_blank">here!</a></h3>

<br><br>

This function returns the state FIPS CODE and the State Name in a dictionary as ''01': 'Alabama','
<br>
```rb
def getStates():
    "Function to return a dict of FIPS codes (keys) of U.S. counties (values)"
    d2 = {}
    r = requests.get("https://www2.census.gov/geo/docs/reference/state.txt")
    reader = csv.reader(r.text.splitlines(), delimiter='|')
    reader_list = list(reader)
    for line in reader_list[1:]:
        d2[line[0]] =  line[2]
    return d2
```
<br>

This function returns the county FIPS CODE and the County Name in a dictionary as ''Autauga': '01001','
<br>
```rb
def getCounties():
    "Function to return a dict of FIPS codes (keys) of U.S. counties (values)"
    d = {}
    r = requests.get("http://www2.census.gov/geo/docs/reference/codes/files/national_county.txt")
    reader = csv.reader(r.text.splitlines(), delimiter=',')    
    for line in reader:
        d[line[3].replace(" County","")] =  line[1] + line[2]
    return d
```
<br><br>

<a href="https://www.buymeacoffee.com/sabioguitaS" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
