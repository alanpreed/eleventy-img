# eleventy-img

Low level utility to perform build-time image transformations.

## Installation

```
npm install @11ty/eleventy-img
```

## Usage

```js
module.exports = function(eleventyConfig) {
  eleventyConfig.addJavaScriptFunction("responsiveImage", function(src, options) {
    return imgResize(src, options);
  });
};
```

### Options

```js
{
	// Path to image file
	src: null,

	// Array of widths, use falsy value to fall back to native image size
	widths: [null],

	// Pass any format supported by sharp
	formats: ["webp", "jpeg"], //"png"

	concurrency: 10,

	// pathPrefix
	urlPath: "/img/",

	// Directory to write to
	outputDir: "img/"
}
```

### Sample return object

Use this object to generate your responsive image markup.

```js
{ webp:
   [ { format: 'webp',
       width: 1280,
       height: 853,
       url: '/img/9b186f9b.webp',
       sourceType: 'image/webp',
       srcset: '/img/9b186f9b.webp 1280w',
       outputPath: 'img/9b186f9b.webp',
       size: 213802 },
     { format: 'webp',
       width: 350,
       height: 233,
       url: '/img/9b186f9b-350.webp',
       sourceType: 'image/webp',
       srcset: '/img/9b186f9b-350.webp 350w',
       outputPath: 'img/9b186f9b-350.webp',
       size: 27288 } ],
  jpeg:
   [ { format: 'jpeg',
       width: 1280,
       height: 853,
       url: '/img/9b186f9b.jpeg',
       sourceType: 'image/jpg',
       srcset: '/img/9b186f9b.jpeg 1280w',
       outputPath: 'img/9b186f9b.jpeg',
       size: 276231 },
     { format: 'jpeg',
       width: 350,
       height: 233,
       url: '/img/9b186f9b-350.jpeg',
       sourceType: 'image/jpg',
       srcset: '/img/9b186f9b-350.jpeg 350w',
       outputPath: 'img/9b186f9b-350.jpeg',
       size: 29101 } ] }
```