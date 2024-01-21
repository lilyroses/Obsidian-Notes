# Seinfeld Daily Quotes
#code #ideas  #project

---

## Scraping

Site: https://www.seinfeldscripts.com/seinfeld-quotes.html

- Scrape quotes from homepage
- Scrape quotes from season 4 onwards
	- Use script listings
	- Scrape each LINK from this page from season 4 and on
	- Parse each episodes script page for quotes
	- Show me each quote (and the speaker), and I can decide if it's a good quote or not
	- If i decide it's a good quote, sort it into the "quotes" directory

```python

# Hold all quotes for randomized daily quotes
all_quotes = []

# Hold values for sorting quotes
quote_speakers = ['elaine', 'george', 'kramer', 'jerry']
quote_seasons = list(range(4, 10))

# Sort quotes by season (see sort_quotes func)
season_4_quotes = []
season_5_quotes = []
season_6_quotes = []
season_7_quotes = []
season_8_quotes = []
season_9_quotes = []

# Sort quotes by speaker (see sort_quotes func)
george_quotes = []
jerry_quotes = []
elaine_quotes = []
kramer_quotes = []


def sort_quotes(all_quotes_list, sort_by=''):
	# Sort by values:
		# 'speaker'
			# value='jerry|george|elaine|kramer'
		# 'season'
			# value='4|5|6|7|8|9'
	if sort_by:
		if sort_by == 'speaker':
			quote_speaker = input('Whose quotes would you like to view? (Choices: Elaine, George, Kramer, Jerry): ')
			if quote_speaker.lower() not in quote_speakers:
				print('Error: Not a valid character.')
				
			for quote in all_quotes_list:
				if quote['speaker'] == 
	for quote in all_quotes_list:
		if 

# Use JSON?
quote_4_1_1 = {
	'season': 4, 
	'episode': 1,
	'speaker': George,
	'quote': '...',
	'img_file': '',ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff
ffffffffffffff}f

fdfefff fufpfdaftfef_fcfhfafrafcftfefrf_fqfuoftfef_flfifsftsf(fqfufoftfef):f
f	fifff f'fgefofrfgfef'f finf fqfufoftfef['fsfpfefafkfefr'f]f.flfofwfefr(f)f:f
f	f	fGfeofrfgfef[f'fqfufotfefsf'f]f.fafppfefnfdf(fqfufotfef)f
f	feflfiff f'feflfafifnef'f fifnf fqfuoftfef[f'fsfpfeafkfefrf'f]f.flofwfefrf(f)f:f
	f	fEflfaine['quotes'].append(quote)
	elif 'jerry' in quote['speaker'].lower():
		Jerry['quotes'].append(quote) 
# quotes can be sorted
```