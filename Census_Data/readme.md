<h1>Get County and States FIPS Code and Name</h1>
<h2>The code samples are set up as user-defined functions</h2>
<h3>The original code this was adapted from can be found <a href = "https://gist.github.com/cjwinchester/a8ff5dee9c07d161bdf4" target="_blank">here!</a></h3>

<br><br>

For the code to function, you need to import the following Modules:
<br>
```rb
import requests
import csv
import json
```
<br>

This function returns the state FIPS CODE and the State Name in a dictionary as "<b>'Alabama': '01',</b>":
<br>
```rb
def getStates():
    "Function to return a dict of FIPS codes (keys) of U.S. counties (values)"
    d2 = {}
    r = requests.get("https://www2.census.gov/geo/docs/reference/state.txt")
    reader = csv.reader(r.text.splitlines(), delimiter='|')
    reader_list = list(reader)
    for line in reader_list[1:]:
        d2[line[2]] =  line[0]
    return d2
```
<br>

This function returns the States FIPS code as a key and then the county FIPS CODE and the County Names for that states as a value in a dictionary: it resemble the following "<b>{'01': {'Autauga': '001', 'Baldwin': '003',...</b>":
<br>
```rb
def getCounties():
    r = requests.get("http://www2.census.gov/geo/docs/reference/codes/files/national_county.txt")
    reader = csv.reader(r.text.splitlines(), delimiter=',')
    d={}
    for line in reader:
        if line[1] not in d:
            d[line[1]] = {line[3].replace(" County", ""): line[2]}
        else:
            d[line[1]][line[3].replace(" County", "")] = line[2]
    return(d)
```
<br><br>

<a href="https://www.buymeacoffee.com/sabioguitaS" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
