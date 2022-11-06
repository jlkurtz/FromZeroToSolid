## Some Experimentation

My goal is to tinker with one or two web applications, see how they work, and identify a possible theme or target solution for this project.

Possible apps
* Word Game
* Bird Browser
* Multilingual Document Browser
* Web Fued
* Drive Every Road or Find the Road Undriven

In the end I did a lot of tinkering.  More than was necessary. Here are some notes on that exercise.

### Word Game

I enjoy playing Boggle and have used some online versions of the game. The grid-based word game has you traversing letters in the grid to create words. The longer the word the higher the points. 

Some features I'd want to add, mainly for after playing a round (on paper):
* Type words and confirm they are valid
* Show solutions as you type
* Show solutions that include letter combinations not at the beginning of a word

To get a feel for what would be entailed for some of these features, I modified the word game in the resources list below. Since the solutions requires knowledge of valid words, I found a Scrabble word list.  I created a Trie data structure to check for valid words. I used a subset of the words just to see how modifying the JavaScript felt.

I found it helpful to use the browser's developer tools console to try things out. And setting breakpoints and exploring the variable values helped understand what variables were in scope. I added trie initialization code and steps to check the trie when a word was submitted. It took a few tries with some exceptions being thrown, but I got it to work to my satisfation. 

**Resources**

[Boggle 5x5](https://www.puzzle-words.com/boggle-5x5/): Full featured word game
[Beautify CSS](https://www.cleancss.com/css-beautify/): Beautify HTML: emacs, sgml-pretty-print
[Beautify JS](https://beautifier.io/)
[Boggle Cube Redesign](http://www.bananagrammer.com/2013/10/the-boggle-cube-redesign-and-its-effect.html)
[Ruby Boggle Solver](https://github.com/cespare/boggle-solver)
* Includes English word list of words up to 15 letters long
  * **(Incorrect)** Shell commands to get the 2 and 3 let words from the word list

        > cat sowpods.txt | colrm 4 > sowpods-three.txt
        > awk '!seen[$0]++' sowpods-three.txt > sowpods-three-distinct.txt
        > wc -l sowpods.txt sowpods-three-distinct.txt
            267751 sowpods.txt
            3688 sowpods-three-distinct.txt
            271439 total

  * **(Correct)** Shell commands to get the 2 and 3 let words from the word list
  
        > grep -E '^.{2,3}$' sowpods.txt > sowpods-two-and-three.txt
        > wc -l sowpods-two-and-three.txt
            1416 sowpods-two-and-three.txt

Scrabble Word Lists
* [Collins Scrabble Words](https://en.wikipedia.org/wiki/Collins_Scrabble_Words)
* [Official Scrabble Word List 2020 - US and Canada](http://www.scrabbleplayers.org/w/NWL2020)
* [European Word List](https://www.wordgamedictionary.com/sowpods/download/sowpods.txt)
* [US Word List](http://www.wordgamedictionary.com/twl06/download/twl06.txt)
* [English Word List](http://www.wordgamedictionary.com/english-word-list/download/english.txt)
* [Scrabble Disctionary API Access](http://www.wordgamedictionary.com/api/)

Trie structure find words as you type 
* [Data Structures 101: Advanced Data Structures in JavaScript](https://www.educative.io/blog/data-structures-tutorial-advanced)

Simple Python Web Server
* `python -m SimpleHTTPServer 8000`

### Bird Browser

Visual and interactive

I fancy bird watching from time to time. My binoculars are tiny and my skill in identifying birds is poor. But I do appreaciate the information I find online about these fine feathered friends.

For this experiment, I'm looking to find a multi-page web site with an interesting layout and design. I'd like to see good examples of HTTML and CSS and see if I can make some simple adjustments.

I tried running the All About Birds site locally, but wasn't able to get all the necessary resources setup.

I then found an HTML template that's bird related and used that as a starting point. See the Birdim HTML template below. I tinkered with some of the CSS. It used Bootstrap and a carausol, but I did not modified or experiment with either of those.  


**Resources**

[Birdim HTML](https://html.design/download/birdim-bird-care-html-template/)
[Birdor PSD](https://html.design/download/birdor-bird-psd-template/)
[All About Birds](https://www.allaboutbirds.org/) - by The Cornell Lab of Ornighology
[All About Birds - Bird Guide](https://www.allaboutbirds.org/guide/)
[eBird](https://ebird.org/home) - An app from The Cornell Lab of Ornighology focused encouraging community birding
[HTML `<aside>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/aside) - used for ads 
[HTML `<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section) - should almost always have a heading
[BirdPress 2](https://themesinfo.com/birdpress2-template-wordpress-cnpba) - WordPress theme used by All About Birds
[Birds of the World](https://birdsoftheworld.org/bow/home) - Range maps for All About Birds

**Sample images**
[Dummy Images](https://dummyimage.com/)
[Vulture?](https://i.picsum.photos/id/1024/1920/1280.jpg) - Niko Virtanen - [Info](https://picsum.photos/id/1024/info)
[Flock of Birds](https://i.picsum.photos/id/258/4608/3072.jpg) - Fré Sonneveld - [Info](https://picsum.photos/id/258/info)
[Cormorant ?](https://i.picsum.photos/id/50/4608/3072.jpg) - Tyler Wanlass - [Info](https://picsum.photos/id/50/info)
[Eagle in Mountains](https://i.picsum.photos/id/538/4096/2713.jpg) - Julia Revitt - [Info](https://picsum.photos/id/538/info)
[Swans and Seagulls](https://i.picsum.photos/id/611/1920/1280.jpg) - Patryk Sobczak - [Info](https://picsum.photos/id/611/info)
[Northern Flicker Male](https://flic.kr/p/AMDgv8) - Jerry McFarland
[Northern Flicker Male](https://flic.kr/p/zx7dAq) - Jerry McFarland
[Northern Flicker Female](https://flic.kr/p/NgHATh) - Jerry McFarland
[Northern Flicker Male](https://flic.kr/p/sc7PDo) - Mick Thompson
[Northern Flicker Female](https://flic.kr/p/GPeTPm) - Mick Thompson
[Northern Flicker Male and Babies](https://flic.kr/p/27vcut9) - Dan Streiffert

### Multilingual Article Browser

Search, browse and personalize. 

I experimented with Arabic, to see how right-to-left languages are handled. It took a couple iterations before I could get the rendering to work. It's essential to include a Content-Type meta tag to indicate the content type is UTF-8
[http-equiv](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta#attr-http-equiv)

    <meta http-equiv="Content-Type" content="text/html;charset=UTF-8">

And tags can use `dir` to control right-to-left handling.

    <body dir="rtl">


Sample HTML

    <!DOCTYPE html>
    <html lang="ar" xml:lang="ar">
      <head>
        <title>جريدة الوطن - Newspaper Al Watan Qatar</title>
        <meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
      </head>
      <body dir="rtl" lang="ar">
        <main>
          <p style="color:#e0e0e0;font-size:20px;">رَبٍّ زِدْنٍي عِلمًا</p>
          <div>
            <div class="widgetTitle">
              <div class="title">كتاب الوطن</div> <a class="link"                             title="المزيد" href=https://www.al-watan.com/كتاب-وأراء > أقرأ
                المزيد
              </a>
            </div>
        </main>
      </body>
    </html>

**Resources**

[Acadmic Corpora](https://www.clarin.eu/resource-families/corpora-academic-texts)
[Arabic Corpora](https://sourceforge.net/projects/arabiccorpus/)
[Arabic Khaleej Corpus - News articles](https://sites.google.com/site/mouradabbas9/corpora/text-corpora?authuser=0) - Corpus used for topic identification. "Punctuation has been deleted"
[Arabic Watan Corpus - News articles]() - punctuation included
[Arabic ANT Corpus](https://antcorpus.github.io)
[Al-Watan](https://www.al-watan.com/) - Daily Arabic language newspaper published in Doha, Qatar.

### Web Fued

[Syntax](https://syntax.fm/show/525/2022-css-trends-and-usage-web-almanac) inspired Family Fued style game where contestants try to pick the top ten trends from the [Web Almanac](https://almanac.httparchive.org/en/2022/).

I imagine this will require some javascript. I found this [clock example](https://codepen.io/jasonleewilson/pen/gPrxwX) that shows how to animate a clock using javascript.

### Drive Every Road or Find the Road Undriven

This one is data intensive and probably not the so climate friendly. Did you ever go for a drive and want to take a route you've never driven, see sights you haven't seen before, or visit friends you haven't visited before (maybe this won't help).

Google Maps allows you to export [your data](https://myaccount.google.com/yourdata/maps).


## Other Resources


### For Prototyping

[httpbin.org](http://httpbin.org/) for simulating HTTP traffic offered by [Kenneth Reitz](https://kennethreitz.org/)

### For Designing

[Pendot](https://pendot.app) - a Figma alternative
[Gimp](https://www.gimp.org/) - installed for PSD
[Photoshop to Figma Switch](https://okbinteractive.studio/en/insights/this-is-why-we-switched-from-photoshop-to-figma-to-make-our-web-prototypes) - explanation of moving from Photoshop to Figma for web protypes

### Javascript Tools I'm Hearing About
[HatTip](https://github.com/hattipjs/hattip) - "HatTip is a set of JavaScript packages for building HTTP server applications."
[TanStack](https://tanstack.com/) - "High-quality open-source software for web developers"
[tRPC](https://trpc.io/) - "End-to-end typesafe APIs made easy"
[Zod](https://github.com/colinhacks/zod) - "TypeScript-first schema validation with static type inference"
[fontaine](https://github.com/unjs/fontaine) - "Automatic font fallback based on font metrics"

### Javascript Conferences and Articles
[Vite Conf](https://viteconf.org/) - "Making Web Development Instant"
[Vite Conf 2022 Replay](https://viteconf.org/2022/replay)
[From Static to Interactive: Why Resumability is the Best Alternative to Hydration](https://www.builder.io/blog/from-static-to-interactive-why-resumability-is-the-best-alternative-to-hydration)
[ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/) -

### Markdown
[Dillinger - Online Markdown Editor](https://dillinger.io/)
[Markdown Guide](https://www.markdownguide.org/)

### Git and GitHub
[Create a repository](https://docs.github.com/en/get-started/quickstart/create-a-repo)
[Creative Commons License](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)
[Git How it Works - Pluralsight](https://app.pluralsight.com/library/courses/how-git-works)

*Example Commands*

* Use cat command as pager for all commands, instead of less
    > git config --global core.pager cat
* 
