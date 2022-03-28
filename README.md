# Fedi-image-scraper

## How to get started
 1. Read [how to install the UiPATH Studio](https://uipath.tistory.com/81) and download the Studio version.

2. Git clone
```
$ git clone https://github.com/skguma/Fedi-image-scraper.git
```

3. Execute `.XAML` files in each folder (You can run it by double-clicking it)

4. Please modify the following variables and arguments to suit your environment.  

<br/>

**AccountImage > Main.xaml > variables tab**
```
- "baseURL": folder path where the scraped image is stored

- "imageDataExcelFile": Excel file name to store the account where the image was uploaded and the tweet data.

- "savePath": Folder path where the list of accounts you scraped will be stored

- "excelFileName" : Excel file name to store the scraping account list
```

<br/>

**Retweets & Likes > Main.xaml > arguments tab**

```
"InputArgument" > "tweetUrl": Tweet url that you want to scrap the list of likes/retweets accounts (InputArguments is JSON Array type, and tweetUrl is the key)
```

<br/>

**ReportTweet > Main.xaml > arguments tab**

```
"InputArgument" > "tweetUrl": Tweet url that you want to report on Twitter (InputArguments is JSON Array type, and tweetUrl is the key)
```

## Directory
### AccountImage  
Creating accounts list obtained from search results and Scraping image dataset

### Retweets & Likes 
Scraping `AccountId`, `AccountName`, `TweetUrl` of accounts that clicked likes and retweets in original tweets

### ReportTweet 
Report the accounts selected by the user on Twitter
