## Weather Data WebScraper
Webscraping is illegal but here is the sample code if you want to use it for non commercial purposes.

### Check out the code below 

```markdown

import requests
from bs4 import BeautifulSoup
page = requests.get("http://forecast.weather.gov/MapClick.php?lat=37.7772&lon=-122.4168")
soup = BeautifulSoup(page.content,'html.parser')
seven_day = soup.find(id="seven-day-forecast")
period = seven_day.select(".tombstone-container .period-name")
period_tags = seven_day.select(".tombstone-container .short-desc ")
temp = seven_day.select(".tombstone-container .temp")
periods = [pt.get_text() for pt in period_tags]
period_days =[d.get_text() for d in period]
temperature =[t.get_text() for t in temp]
short_desc =[f["title"] for f in seven_day.select(".tombstone-container img")]
print (short_desc)
print(periods)
print(temperature)
print (period_days)


