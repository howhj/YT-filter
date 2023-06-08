# YT-filter
A uBlock Origin filter to revert some of the changes YouTube made to the subscription page.

## How to Use

1. Install the uBlock Origin extension.

* [Firefox](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
* [Chrome](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm)
* [Edge](https://microsoftedge.microsoft.com/addons/detail/ublock-origin/odfafepnkmbhccpbejgmiehpchacaeak)
* [Opera](https://addons.opera.com/en/extensions/details/ublock/)
* [Manual install](https://github.com/gorhill/uBlock/releases)

2. Click on the extension, then the gears icon.
3. Navigate to "My filters".
4. Click on "Import and append", then select the `YT_subscriptions_filter.txt` file.
5. Click "Apply changes".
6. Refresh the Youtube subscription page.

## Original Script
[Click here](https://www.reddit.com/r/uBlockOrigin/comments/11nrqy3/youtube_homepage_3_videos_per_row_issue/) for the original filter by u/archangelique.

From the Reddit post:

> First 2 rules are for 4 videos per row,
>
> 3-4th are for Channel page margin fix on the 4th column,
>
> 5-6th are for font size and line height,
>
> 7th is for removing annoying horizontal scrollbar,
>
> 8th is for keeping menu closed to have more space for videos. This one prevents the menu from opening even when you click on it for now. If you often use the menu, exclude this filter or simply add an exclamation mark "!" at the beginning of this line.
>
> 9th is for Search results video thumb size fix, reverts back to way smaller thumb size."

Note that the 8th rule is already commented out in this script.

The line after the 9th rule is taken from u/mborsik's [comment](https://www.reddit.com/r/youtube/comments/13xut1e/comment/jna9ger/).

## Changes

* `youtube.com##ytd-rich-grid-renderer:style(width: 80% !important; padding-left: 110px !important;)`

  Adjusts the horizontal position of the video grid in the webpage. Removing this line will cause the grid to take up the full space available.

  Note that I tuned this to the window size I normally use, so this wouldn't provide accurate positioning in other window sizes (e.g. maximised).

* `youtube.com##div.ytd-rich-grid-renderer:style(padding-top: 0px !important;)`

  Removes the extra padding above the top element (the one containing the "Latest" text, "Manage" button, and grid/list view toggle).

* `youtube.com###content.ytd-rich-section-renderer:style(margin: 0 0px !important;)`

  Removes the horizontal padding for the top element.

* `youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row:style(margin-left: 0px !important; margin-right: 4px !important; margin-bottom: 24px !important; width: 210px !important;)`

  Reduces the margins around each video element (containing the thumbnail, title etc.), packing them together more tightly.

* `youtube.com##h3.ytd-rich-grid-media:style(margin: 8px 0 8px !important;)`

  Adjusts the margin for the video title, so that it is closer to the video and further from the channel name.

* `youtube.com###details > .ytd-rich-grid-media.style-scope.yt-simple-endpoint`

  Removes the channel's avatar in each video element, giving the video title more space.
