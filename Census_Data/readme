<h1>Get County and States FIPS Code and Name</h1>
<h2>The code samples are set up a user-defined functions</h2>

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
