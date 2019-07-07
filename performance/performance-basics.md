# Performance

There are **3 areas of improvement**:

1) Client-side
2) Network transfer
3) Server-side

### Improving Client-Side Performance

* Minimize text in the js, css, and html files
  * Tools: UglifyJS
* Minimize images
  * One way to minimize an image is to pick the best file format
    * jpg, svg, gif, png
  * jpg
    * photos, images, things with many colors 
    * con: 
      * don't allow for transparency (only pngs and gifs allow transparency)
      * A little big on file size
  * gifs
    * cons:
      * grainy
      * oddly colored (because colors are limited)
    * pros:
      * less color -> smaller file size
      * good for small animations
  * pngs
    * smaller in file size than jpg
    * limits colors
    * can have transparency
  * svg
    * vector graphics
    * can expand and shrink without impacting clarity
    * incredibly small
    * can be customized with css, too
    * tend to be simplistic with few colors 
  * GOAL:
    * pick the right file format
    * minimize as much as possible without limiting quality
  * TIPS & TOOLS
    * reduce png with TinyPNG
    * reduce jpg with JPEG-optimizer
    * Lower jpeg quality 30-60%
    * resize image based on size it will be displayed
      * match resolution to that being displayed on the site
      *  if css width is x px wide, cut the image down to that width
    * display different sized images for different backgrounds
      * **use media queries**
      * the browser downloads only what it needs, so if a certain image is only visible at a certain screen size, only then will the browser download it. Otherwise, the image is not fetched
    * use CDNs like imigx
    * remove image metadata 