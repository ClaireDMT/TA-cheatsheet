# IMAGES 

## **IMAGES ON PRODUCTION**

### Images not showing on production

1. If the image is rendered in the HTML, make sure you use the Rails image_tag  helper rather than manually writing an HTML <img>  tag
2. If the image is a background image or whatever and is in your CSS file, use the Rails image-url helper instead of writing a normal CSS url
3. Make sure in either case that the file extension (PNG, JPG, whatever) is included

**Also don’t forget that Cloudinary is only for images that the user uploads. There is no need to use it otherwise. Any static images should always come out of your asset pipeline (be located in the Rails assets folder)**
[Asset Pipeline](https://guides.rubyonrails.org/asset_pipeline.html)
