# Kissu-JSON-API-Docs
JSON API documentation for kissu.moe. This file contains information on both JSON created for the Kissu-UI (done on the Hazuki API engine) and the Vichan-UI. Documentation provides a link to an example file and then explains the information within. Information within could be changed at any time.

## Kissu-UI / Hazuki API Style
### /api/properties/{BOARD}.json
https://kissu.moe/api/properties/b.json
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
## Vichan-UI / Vichan API Style
