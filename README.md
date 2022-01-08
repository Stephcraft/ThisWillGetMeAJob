# This Will Get Me A Job
*This code will provide me a summer internship in the United States.*

It is a chrome extension that saves all the pertinent information from job postings to a google sheet. The google sheet acts as a tracking tool for all the applied jobs:
- Applied
- Got ghosted?
- Got an interview, went well?
- Got an offer, accepted the offer?
- Got a Job!

It also has many filters, statistics and rankings.

### TODO list
- [ ] Upload the code without api keys
- [ ] Rename repository to `ThisGotMeAJob`

### Supported platforms
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/linkedin-square.svg width=18> LinkedIn
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/stack-overflow.svg width=18> Stackoverflow

## Design
![image](https://user-images.githubusercontent.com/23728346/148632037-9c129025-633b-4f45-bd96-f10e8a2156a1.png)

## Job data
These are data points collected for each job:
```py
# company info
company {
    name
    website
    logo
    size
    founded
    industry
}

# platform info
platform
website

# job info
position
type
workspace
location
salary

# timing
posted_date
applied_date

# additional info
description
comment
```

## Web scrapper utility
I had found no great way to do web scrapping from a chrome extension, so I created my own utility:
```js
var result = await WebScrapping.scrape('https://awesome.url/page', 'cool_scrapper_content.js')
```

<img src=https://cdn.discordapp.com/attachments/581863115843567616/922333917376311386/Untitled_Diagram.drawio.svg>
