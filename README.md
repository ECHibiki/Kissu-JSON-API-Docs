# Kissu-JSON-API-Docs
JSON API documentation for kissu.moe. This file contains information on both JSON created for the Kissu-UI (done on the Hazuki API engine) and the Vichan-UI. Documentation provides a link to an example file and then explains the information within. Information within could be changed at any time.

## Kissu-UI / Hazuki API Style
### /api/properties/banners.json
https://kissu.moe/api/properties/banners.json <br/>
A list of all the banners submitted to banners.kissu.moe.
- ARRAY :: Array containing all the banners
  - STRING url :: The URL which clicking on the image goes to. Ignorable on small banners.
  - STRING uri :: The URI to display the image.
  - STRING name :: The username of the image creator.
  - STRING size :: The size of the banner (small, wide).
  - INT clicks :: The number of clicks on the banner. Ignorable on small banners.
  - STRING board :: If the banner was created to only be displayed on certain boards, then this field will contain said board

### /api/properties/site.json
https://kissu.moe/api/properties/site.json <br/>
A list of information about the website.
- BOARD-ARRAY boards :: An array of public boards.
  - STRING name :: The name of the board.
  - STRING title :: The title of the board.
  - STRING topic :: The topic associated with the the board.
  - STRING category :: The categorization used for grouping the board with others.
- FRIENDS-ARRAY friends :: An array of websites associated with the imageboard.
  - STRING name :: The name of the partner.
  - STRING descrption :: How to describe this partner.
  - STRING media :: A thumbnail that describes this partner.
  - STRING url :: THe url which this partner site can be accessed with.
- NEWS-DETAILS news :: Details of website news.
  -  STRING message :: The news message.
  -  STRING href :: A URL that clicking on the site logo will go to.
  -  INT updated_at :: A unix timestamp of when the news was last updated.
- STATS-DETAILS stats :: A basic summary of website statistics.
  - STRING posts :: The number of posts on the website.
  - STRING unique :: The number of unique posts on the website.
  - STRING data :: A value representing the amount of website data stored only on the API server.

### /api/properties/error.json
https://kissu.moe/api/properties/error.json <br/>
Very simple page for the error page information.
- BANNER-ITEMS banner :: Contains banner objects representing the page's current banner.
  - BANNER-ITEM size :: Values of "small" or "wide" contain information about the given banner.
    - STRING url :: The URL which clicking on the image goes to. Ignorable on small banners.
    - STRING uri :: The URI to display the image.
    - STRING name :: The username of the image creator.
    - STRING size :: The size of the banner (small, wide).
    - INT clicks :: The number of clicks on the banner. Ignorable on small banners.
    - STRING board :: If the banner was created to only be displayed on certain boards, then this field will contain said board
- STRING title :: The page title which this file belongs to.
- STRING title_descriptor :: The description of the page which this file belongs to.

### /api/properties/home.json
https://kissu.moe/api/properties/home.json <br/>
Contains information on the home page.
- BANNER-ITEMS banner :: Contains banner objects representing the page's current banner.
  - BANNER-ITEM size :: Values of "small" or "wide" contain information about the given banner.
    - STRING url :: The URL which clicking on the image goes to. Ignorable on small banners.
    - STRING uri :: The URI to display the image.
    - STRING name :: The username of the image creator.
    - STRING size :: The size of the banner (small, wide).
    - INT clicks :: The number of clicks on the banner. Ignorable on small banners.
    - STRING board :: If the banner was created to only be displayed on certain boards, then this field will contain said board
- ACTIVE-ARRAY active :: A lsit of active threads on the website.
  - INT no :: The number of the post
  - STRING com :: The text identifying the thread. Could be a filename or a plaintext snippet of the comment.
  - STRING file_id :: A string representing how the thumbnail is stored.
  - EMBED-OBJECT embed :: If there's an embed this will contain the information on it.
    - STRING site :: What site does the embed belong to.
    - STRING code :: What code is the file stored with.
    - STRING inputURL :: What was the URL which the poster used to post the embed.
    - STRING time :: The second at which the video is supposed to start.
  - STRING board :: The thread's board.
- FEATURED-ARRAY featured :: A list of threads that have been deemed high quality by the staff.
  - INT no :: The number of the post
  - STRING com :: The text identifying the thread. Could be a filename or a plaintext snippet of the comment.
  - STRING file_id :: A string representing how the thumbnail is stored.
  - EMBED-OBJECT embed :: If there's an embed this will contain the information on it.
    - STRING site :: What site does the embed belong to.
    - STRING code :: What code is the file stored with.
    - STRING inputURL :: What was the URL which the poster used to post the embed.
    - STRING time :: The second at which the video is supposed to start.
  - STRING board :: The thread's board.
- STRING title :: The page title which this file belongs to.
- STRING title_descriptor :: The description of the page which this file belongs to.

### /api/properties/{BOARD: [a-zA-Z]+}.json
https://kissu.moe/api/properties/b.json<br/>
Information about the given board is stored in the properties folder.
- BANNER-ITEMS banner :: Contains banner objects representing the page's current banner.
  - BANNER-ITEM size :: Values of "small" or "wide" contain information about the given banner.
    - STRING url :: The URL which clicking on the image goes to. Ignorable on small banners.
    - STRING uri :: The URI to display the image.
    - STRING name :: The username of the image creator.
    - STRING size :: The size of the banner (small, wide).
    - INT clicks :: The number of clicks on the banner. Ignorable on small banners.
    - STRING board :: If the banner was created to only be displayed on certain boards, then this field will contain said board
- STRING board :: The board this properities file belongs to.
- STRING title :: The page title which this file belongs to.
- STRING title_descriptor :: The description of the page which this file belongs to.
- STRING presentation :: The way that information is displayed for this page. Values of postboard, fileboard, scoreboard or pollboard.
- STRING new_post_counter :: A value that goes up every time someone posts without sage.
- FEED-ARRAY new_post_feed :: An array of actions done on the board.
  - INT no :: The number of this post.
  - INT resto :: The thread this post replies to.
  - STRING board :: The board this post belonged to.
  - INT time :: The time which this action occured.
  - INT sage :: If the user used sage this value is 1, otherwise 0.
  - INT deleted :: If this post was deleted this value is 1, otherwise 0.
- INT thread_count :: The number of threads on the board.

## /api/threads/summary.json
https://kissu.moe/api/threads/summary.json? <br/>
A list of the most recently added posts to the website. Only contains posts from the public boards.
- SUMMARY-ARRAY recent :: The list of recent posts.
  -  INT no :: The number of the post.
  -  INT resto :: The number of the thread this post belongs to.
  -  STRING com :: The text which identifies the most recent post. Can be a filename or a plaintext snippet of the comment.
  -  INT time :: The time it was posted.
  -  STRING board :: The board this post belongs to.
  -  STRING-ARRAY cites :: A list of the board+number of posts this given post is referencing. Format of "[a-z]+\-[0-9]+" for example: "qa-4165".

### /api/threads/{BOARD: [a-zA-Z]+}/catalog/{PAGE: [1-9]+ OR full}.json
https://kissu.moe/api/threads/b/catalog/full.json <br/>
Information about the given catalog is stored in partial forms on pages or the full form. The partial is split up into chunks of 60 threads each.
- ARRAY :: By default threads are ordered based on the last bump.
  - INT no :: The number of this post.
  - INT resto :: The thread this post replies to.
  - STRING com :: The thread's OP comment.
  - STRING mod_com :: In the case that this post was edited by a moderator this field will be used instead. it will be a raw HTML input.
  - STRING ban_message :: The ban message associated with the post.
  - STRING capcode :: When a staff member identifies themselve's their status will be placed here.
  - STRING tripcode :: When a community member uses a tripcode it will be placed here.
  - INT score :: In the case of scoreboards and image posts, this field will have a value representing the community score of the image. 
  - STRING tag :: In the case of fileboards this field will have a character representing it's categorization.
  - POLL-OBJECT poll :: In the case of pollboards this field will have the information of the given poll
    - POLL-QUESTIONS-ARRAY questions :: An array of the poll questions.
      - STRING text :: The text of the question.
      - STRING color :: The color hex for the questions visualization.
      - INT responses :: How many people voted for this option.
    - STRING type :: Is this a multiple choice or a single choice poll?
    - INT-ARRAY timeLeft :: An array where the first value is the timestamp the poll was created and the second the time when it expires.
  - STRING title :: The thread's title (autogenerated based on the comment or filename).
  - STRING sub :: The thread's subject.
  - STRING name :: The OP's name.
  - INT time :: The time of creation.
  - INT locked :: Is this thread locked? 1 if yes, 0 if no.
  - INT sticky :: Is this thread supposed to be at the top of the catalog? 1 if yes, 0 if no.
  - INT zombie :: Is it a permanent thread? 1 if yes, 0 if no.
  - INT sage :: This thread can not be bumped? 1 if yes, 0 if no.
  - INT cyclical :: Posts removed as new replies are made? 1 if yes, 0 if no.
  - INT bumplimit :: Is the post at bumplimit? 1 if yes, 0 if no.
  - INT imagelimit :: Is the post at imagelimit? 1 if yes, 0 if no.
  - INT last_modifed :: The time of the last post which caused a bump to be triggered.
  - INT tn_h :: The thumbnail height.
  - INT tn_w :: The thumbnail width. 
  - INT h :: The full file height.
  - INT w :: The full file width.
  - INT static_thumb :: If this thumb is a static file then it will be a 1.
  - STRING spoiler :: If the file is spoilered, it will contain the spoiler type used for the file.
  - STRING board :: The board the thread belongs to.
  - INT fsize :: The data size of the file.
  - STRING filename :: The filename of the file.
  - STRING ext :: The extention of the file.
  - EMBED-OBJECT embed :: If there's an embed this will contain the information on it.
    - STRING site :: What site does the embed belong to.
    - STRING code :: What code is the file stored with.
    - STRING inputURL :: What was the URL which the poster used to post the embed.
    - STRING time :: The second at which the video is supposed to start.
  - INT file_id :: The code with which the file was stored to the serveres.
  - STRING location :: Which subdomain is the file located on. Values of haiji or luna.
  - STRING md5 :: The MD5 hash of the file.
  - CITES-ARRAY cites :: An array representing the cites. Cites in this list are posts targetting this given post
    - STRING post :: What's the number of the cite. 
    - STRING board :: Which board does it belong to. 
    - STRING host :: Which thread is hosting this cite.       
  - REPLIES-ARRAY last_replies :: Last few posts on the given thread.
    - INFORMATION IS A REPLICATION OF THE PARENT
    - EXCEPTIONS:
      - There is no reply_count field 
      - There is no tag or poll field. These are for thread starters.
      - There is no sub field.
      - There is no last_modifed field.
      - There is no locked, sticky, zombie, sage or cyclical fields. These are thread modifiers. 
      - There is no last_replies array.
  - INT reply_count :: Number of replies in the thread       

### /api/threads/{BOARD: [a-zA-Z]+}/{THREAD: [0-9]+}/{PAGE: [0-9]+ OR full}.json
https://kissu.moe/api/threads/b/8005/0.json <br/>
Information about the given thread is stored in partial forms on pages or the full form. The partial is split up into chunks of 150 replies each. Page 0 contains the most recents posts and when new replies are made past 150 it populates pages from number 1.json to N.json. This is similar to the above
- ARRAY :: Access this value by looking up array index 0
  - These values are identical to the above section. Instead of copy pasting it I leave you to connect the dots.
  - NEW INFORMATION:
    - ARRAY similar_threads :: An array of threads which are considered similar to the given post.
      - INT
      - STRING
      - STRING mod_com :: When a thread has been modified by moderators it will have a raw HTML input
      - STRING title :: The autogenerated title of the thread.
      - FLOAT tn_h :: Thumbnail's height.
      - FLOAT tn_w :: Thumbnail's width.
      - STRING board :: The thread's board.
      - STRING ext :: The extention of the file (not the thumbnail).
      - STRING file_id :: The id which the file is stored to the server with
      - INT static_thumb :: If this is a static thumbnail then the value will be 1.
      - STRING spoiler :: If this thread is spoilered this will contain the type of spoiler it is.
      - EMBED-OBJECT embed :: If there's an embed this will contain the information on it.
        - STRING site :: What site does the embed belong to.
        - STRING code :: What code is the file stored with.
        - STRING inputURL :: What was the URL which the poster used to post the embed.
        - STRING time :: The second at which the video is supposed to start.

## Vichan-UI / Vichan API Style
