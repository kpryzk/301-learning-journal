# LJ Code 301 - Day 3

I have been fighting with appending portfolio entries to the Skeleton Boilerplate for an hour and finally had a breakthrough. Skeleton provides code to space columns evenly horizontally on a screen larger than 550px, providing the necessary width percentages of the columns AND the spacing. When I was trying to append the jQuery rendered column items, all items were floating left with no spacing. I finally realized that Skeleton's CSS uses the :first-child selector.

<code>@media (min-width: 550px) {
  .container {
    width: 80%; }
  .column,
  .columns {
    margin-left: 4%; }
  .column:first-child,
  .columns:first-child {
    margin-left: 0; }
}</code>

Because I was using a template format to create the portfolio items, and because they were being appended individually, I am pretty sure each of the three items was being given :first-child status! My solution was pretty inelegant - I just added a media query to my styles.css file to override the one provided by Skeleton, and spaced the elements at 2%, meaning they are all basically centered but not taking up the full width of their container.

<code>@media (min-width: 550px) {
  .column:first-child,
  .columns:first-child {
    margin-left: 2%; }
}</code>

I am wondering if there is a better method to somehow get the individual elements created in jQuery to receive individual classes or statuses or, like, whatever so I could differentiate between the first appended and the ones following.
