# web-scraping-for-sentence-mining

In this repository, I gather scripts I use for scraping a bunch of websites whose content I find useful (most are in my native language, but there's also Reverso context, which can be used for any language it supports). Audio is downloaded/generated and then all data is written to .csv files, which I merge then import into Anki. This way, I can create thousands of language learning cards in a few minutes.

**See also:**
[Morphman](https://massimmersionapproach.com/table-of-contents/anki/morphman/) - for dealing with low-yield, repetitive, short/long cards.

## 🏡 Running locally

First, clone the repository and create a virtual environment for the project (to ensure you won't have problems with your libraries versions). Using [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/):

`mkvirtualenv web-scraping-sentences` - Creates virtual environment

`workon web-scraping-sentences` - Activates virtual environment

Then, install all dependencies with `pip install -r requirements.txt`.

If you want to use WaveNet, you need to [get your key on Google Cloud Platform](https://cloud.google.com/text-to-speech/docs/quickstart-client-libraries) and fill it in `api_key.json`, as in `api_key_example.json`.

To scrape Reverso, head to `reverso_scraping/` and refer to `scrap.py`. Input URLs you want to scrape into `scrap_page()`. By default, output will be placed under `audios/` for WaveNet audios and under `csv/` for csv files (the tab character, \t, is used as separator) ready to be imported to Anki. You can also crawl URLs for words and expressions with `crawl_top()`, which can retrieve URLs for common words and expressions, present in rankings generated by Reverso. This function will write URLs into a txt file which can be used with `scrap_pages_multithread()`, written to scrap multiple pages in parallel. A few examples are left commented out in `scrap.py`.
