# ![alt text](https://i.imgur.com/LrV2tLe.png) Novel-Grabber
Novel-Grabber is a GUI based web scrapper that can download and convert chapters into EPUB from various supported web novel sites or from any other site manually.

## Features
- Over 100 supported [sites](https://github.com/Flameish/Novel-Grabber/tree/master/src/main/java/grabber/sources)
- A manual mode for unsupported sites
- Blacklist HTML tags to remove unwanted content
- A library to keep track of new releases for your favorite novels
- Login support via cookies
- CLI

## How to use
### Running the program
Download [Novel-Grabber.zip](https://github.com/Flameish/Novel-Grabber/releases/latest/download/Novel-Grabber.zip) and execute the launcher inside, if you can't execute the jar, try to start it via the terminal command: 

	java -jar NG-Launcher.jar

Starting `NG-Launcher.jar` will update and re-download files. You can also start the main program directly via `Novel-Grabber.jar` inside the `bin`  subfolder.

### Automatic novel downloading
1. Enter the link of the novel
2. Click on 'Check' to fetch metadata and chapter list
3. Choose from various download options / manually adjust metadata 
3. Select chapter range and grab chapters

### Manual novel downloading

#### Using a table of content page
1. Enter the URL to the novel's table of contents page and retrieve all links on the site.
2. Remove all unwanted links from the selection window.
3. Input the chapter container the site uses. I strongly suggest using the "auto detect" function, it generally works well and enables grabbing from different sites.
Or you can [specify a CSS selector manually](https://github.com/Flameish/Novel-Grabber/issues/62#issuecomment-730305855).
4. You can remove unwanted content from the chapter via the "blacklisted tags" window (flag icon at the top). Don't forget to set title, author, cover etc.
 
#### Using Chapter-To-Chapter navigation
1. Input the URL of your starting point and ending point chapter. (inclusive)
2. Input the selector for the "Next-Chapter" button. You want to select the `<a>` tag of it. (via css selector)

### CLI
**Use these arguments with the main `Novel-Grabber.jar` from inside the `bin` folder!**

[] = optional paramaters 
{} = arguments for paramater

| Parameter | Arguments | Description |
| :--- | :---: | :---|
-gui / `none` | | Starts the Graphical User Interface.
-link | {novel_URL} | URL to the novel's table of contents page. Starts download.
[-wait] | {miliseconds} | Time between each chapter grab.
[-headless] | {chrome/firefox/opera/edge/IE/headless} | Visit the website in your browser. Executes javascript etc.
[-chapters] | {all}, {5 27}, {12 last}	| Specify which chapters to download.
[-path] | {directory_path} | Output directory for the EPUB.
[-login] | | Log in on website with saved account. -account is not needed if an account for this domain was added previously.
[-noDesc] | | Don't create a description page.
[-getImages] | | Grab images from chapter body as well.
[-displayTitle]| | Write the chapter title at the top of each chapter text.
[-invertOrder] | | Invert the chapter order.
-help | | Shows the help page.

Example: 

	java -jar Novel-Grabber.jar -link http://host.com/novel/ -chapters 15 last -getImages

### Telegram bot

To host your own Telegram bot you need to add the line `telegramApiToken=your_token ` to your `config.ini` 
or on the GUI via the Telegram Bot settings tab.

By default the bot will read the output for `/info` from a `info.txt` file inside the telegram folder which you can adjust.

To start the bot you need to use the `-telegramBot` parameter:

	java -jar Novel-Grabber.jar -telegramBot

## Screenshots
![Automatic Tab](https://i.imgur.com/xBUdkmL.png)

![Manual Tab](https://i.imgur.com/jDm2ABW.png)

![Library Tab](https://i.imgur.com/8OUQe9E.png)

## Disclaimer & Warning
Most sites prohibit the scrapping for their content. Use at your own risk. 
Please use with appropriate wait times. Downloaded chapters are for private use only.

## Requirements
* [Java](https://www.java.com/en/) (version 8+) needs to be installed.

## Credits & Libraries 
Novel Grabber was build in Java with:

* [jsoup](https://www.jsoup.org/)
* [json-simple](https://code.google.com/archive/p/json-simple/)
* [epublib](https://github.com/psiegman/epublib)
* [webdrivermanager](https://github.com/bonigarcia/webdrivermanager)
* [selenium ](https://selenium.dev/)
* [Simple Java Mail ](https://github.com/bbottema/simple-java-mail/) 
* [Readability4J](https://github.com/dankito/Readability4J)
* [Notify](https://github.com/dorkbox/Notify)
* [icons8](https://icons8.com) 
* [FlatLaf](https://www.formdev.com/flatlaf/)
* [Java Telegram Bot API](https://github.com/pengrad/java-telegram-bot-api/)
