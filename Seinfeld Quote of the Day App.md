# Seinfeld Quote of the Day App
#project

---

## Steps

---

### STEP 1. PRODUCE DATA TO POPULATE APP

---

#### EPISODE/SEASON DATA

##### SOURCE
- **URL:** [seinfeldscripts.com/seinfeld-scripts](https://seinfeldscripts.com/seinfeld-scripts.html)

##### ACQUISITION
- **METHOD #1**: *copy/paste* / *manual*
- **FETCHED BY *(script)*:**- `N/A` 

- **METHOD #2:** `requests` / `soup` object
- **FETCHED BY: *(script)*:** `get_script_links.py`

##### STORAGE (RAW)
- **STORED AS:** `RAW_episode_data.txt`

##### PARSED (RAW)
- **HANDLED BY:** `parse_raw_episode_data.py`
	- *creates dictionary for each episode w/ [[Seinfeld Quote of the Day App#DATA ATTRIBUTES|data attribute]] keys*

##### STORAGE (PARSED)
- `episodes.py`
	- a (`list[dict]`) -> *see [[Seinfeld Quote of the Day App#DATA ATTRIBUTES|data attributes]] for dictionary keys*

---

##### DATA SUBSET METHODS

| Class      | Attribute                | Type                                                                                           |
| ---------- | ------------------------ | ---------------------------------------------------------------------------------------------- |
| `Season`   | `number_of_episodes`     | `int`                                                                                          |
| `Season`   | `air_dates`              | `[list[str]]`                                                                                  |
| `Season`   | `episodes`               | `[list[Episode]]`                                                                              |
| `Season`   | `number`                 | `int`                                                                                          |
| `Season`   | `id`                     | `int` (generated from `number` and ID prefix (`1`))                                            |
| `Episode`  | `season_no`              | `int`                                                                                          |
| `Episode`  | `title`                  | `str`                                                                                          |
| `Episode`  | `id`                     | `int` (generated from `chronological_number` and ID prefix (`2`))                              |
| `Episode`  | `air_date`               | `str` (mm/dd/yyyy)                                                                             |
| `Episode`  | `chronological_no`       | `int`                                                                                          |
| `Episode`  | `number_in_season`       | `int`                                                                                          |
| `Episode`  | `previous`               | `Episode`                                                                                      |
| `Episode`  | `next`                   | `Episode`                                                                                      |
| `Episodes` | `show_all`               | `list[Episode]`                                                                                |
| `Episodes` | `.len()`                 | `int`                                                                                          |
| `Episodes` | `.list_alphabetically()` | returns all `Episode.title` strings sorted alphabetically                                      |
| `Episodes` | `.list_by_season()`      | returns `Season.number` string followed by indented  `Episode.title` strings for each `Season` |

----
##### DATA VALUES

###### REQUIRED
- [ ] episode id
- [x] episode title
- [ ] episode no (by season)
- [x] episode no (chronologically)
- [x] episode air date
- [ ] next episode
- [ ] previous episode
- [ ] season id
- [x] season no
- [ ] no. episodes in season
- [x] season air dates years (start/end)
- [ ] script text file name
- [ ] script link

---
###### PRIMARY DATA (STATIC)
**SEASONS**
- [ ] Season number
- [ ] Season air date year (start/end)

**EPISODES**
- [ ] Episode title
- [ ] Episode air date
- [ ] Chronological episode number

###### INFERRED DATA (SECONDARY/GENERATED)

| VARIABLE            | TYPE        | GENERATED FROM                                      |
| ------------------- | ----------- | --------------------------------------------------- |
| `number_of_seasons` | `int`       | `len(season_headers)`                               |
| `seasons_headers`   | `list[str]` | season header strings (from `RAW_episode_data.txt`) |
|                     |             |                                                     |

- [ ] Number of seasons
- [ ] Number of episodes per season
- [ ] Seasonal episode number
- [ ] Previous episode
- [ ] Next episode
- [ ] Episode ID
- [ ] Season ID
- [ ] Episode script link
- [ ] Script text file name

---

### Script Links

- Source URL: [seinfeldscripts.com/seinfeld-scripts](https://seinfeldscripts.com/seinfeld-scripts.html)

- FETCH METHOD (script links): `requests`

- STORED AS: `seinfeld-scripts.html`


2. [ ] `DATA` folder
	1. `FETCH_RAW_DATA` - the methods used to fetch HTML or other raw data
		1. `fetch_raw_seinfeldscripts_site.html` - use `requests` to fetch the HTML of the site
	2. `RAW_DATA` - copied/pasted or fetched straight from source
		2. `raw_season_info.txt` - unparsed text of episode info
		
		4. `raw_seinfeldscripts_site.html` - fetched with `requests`
		5. 
	3. `GENERATED_DATA` - data files generated from raw data files
		1. `script_links.txt` - a text file of links to episode script pages 
	4. `create_episode_info.py` - creates *`episode_info.py`*
	5. `episode_info.py`  - a Python dictionary of episode info
	6. `create_script_links.py` - creates *`script_links.txt`*

---

## Database

---

### DESIGN

---

#### DATA REQUIREMENTS


---

- **QUOTES**

| PK | INT | quote_id |
| ---- | ---- | ---- |
| FK | INT | episode_id |
| FK | INT | quotee_id |
|  | TEXT | quote_text |
| FK | INT | quote_screenshot_id   |



- **EPISODES**
	- `episode_id` (PK,)
	- `season_id` *

- **SEASONS**
	- season_id 

	- Time stamp when quote occurs in the episode
		- Start time stamp
		- End time stamp
	
	- Timestamp of screenshot
	- 
---

#### TAB