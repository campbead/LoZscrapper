# LoZscraper

This project is analysis of Legend of Zelda (1986) speedruns from [Arcus87](https://www.twitch.tv/arcus87/).  Here I include my Arcus Twitch Vod Scraper (Python), the scaped data, and my analysis (R Markdown)

## Background

I got into watching speedrunner's on Twitch and while back.  In particular I was got into  who was into speedrunning Legend of Zelda (1986), for the NES, a game a played a lot of as a kid.  

Watching him, I thought it would be cool to collect some data on how his speed run was progressing, and I had a few questions: 
- Which rooms give him the most trouble?
- How big a deal is it to have the "beam-sword"?
- How much better is he getting over time?

I have started to blog about this on [Medium](https://medium.com/@campbead) which has more descriptive analysis.  

## Using the scraper
The scraper `scrapeLOZ.py` was really my first attempt doing a Python project and it's not a pretty thing, but it works.  I'm going to document how to use the scraper more fully later but it's not a big priority.  

The scraper works on an .mp4 file downloaded from twitch, I used [Arne Vogel's Concat](https://github.com/ArneVogel/concat) but you're free to use whatever tool you like.  

- "-v" or "--video" `-v='video2scrape.mp4` **required** this specifies the file to scrape
- "--room_list" `--room_list='roomlist.csv'` this specifies the room list to use while scraping, if none is specified this will default to '../data/unique_room_list_double_hundo_with_index.csv' 
- "--verbose" gives more output
- "-t" or "--start" `-t=1000` time in the video to start scraping given in milliseconds 
- "-run" `-run=1345` this species the run number for the first run that begins after your start time 
- "-d" of "--delta" time in milliseconds for advance when initially checking for next room, defaults to 3000

## The data
Output will be an sqlite database .db file of the same name as your video.

## Todo
I'm happy with the current version for my analysis but I may continue to update planned features in the future.

## Planned Features
- [ ] Check to see if video file exists
- [ ] Check if Run ends on Room 1
- [ ] Specify an end time to stop scraping
- [ ] Manual mode for scraping, will not need a room list.
- [ ] No save / continuation feature
- [ ] Adjustable time precision, currently a precision of 0.1 s is used for changes
- [ ] Migrate from tesseract to [opencv template matching](https://docs.opencv.org/2.4/doc/tutorials/imgproc/histograms/template_matching/template_matching.html) for recognition 
