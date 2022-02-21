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

### Supported job board platforms
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/linkedin-square.svg width=18> LinkedIn
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/stack-overflow.svg width=18> Stackoverflow
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/angellist.svg width=18> AngelList
- <img src=https://cdn.icon-icons.com/icons2/2389/PNG/512/indeed_logo_icon_145170.png width=18> Indeed
- <img src=https://raw.githubusercontent.com/Rush/Font-Awesome-SVG-PNG/3cfbcdaff9818c3e2c07d755d556fe1f34d7cf0d/black/svg/google.svg width=18> Google jobs search

### Supported autofill platforms
- <img src=https://user-images.githubusercontent.com/23728346/150831428-9ffedc81-ee87-4899-8b15-a7f71930e2f3.svg width=16> MyWorkdayJobs


## Design
![image](https://cdn.discordapp.com/attachments/581863115843567616/932814886969430036/Job.drawio_1.svg)

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

## Web scrapper utility v2
Instead of relying on iframes which tend to cause many COORS errors and slowlyness. V2 utilises `fetch` instead.

###### Content.js
```js
async function request(method, url, other) {
    return await BackgroundTasks.execute('request', { method, url, other })
}

var html = await request('GET', 'https://awesome.url/page', { cache: 'force-cache' })
var doc = HTML.toElement(`<document>${html}</document>`)
// either simulate into an iframe or process the initial source code data...
```

###### Background.js
```js
function request(method, url, other) {
    // request logic with fetch...
}

BackgroundTasks.addHandeler('request', async (params) => {
    var { method, url, body, other } = params
    return await request(method, url, other)
})
```
