# Weaverjs | Web starter kit

Weaverjs is an opinionated boilerplate for web development based on [Gulp](http://gulpjs.com/), [Node](https://nodejs.org/), [NPM](https://www.npmjs.com/), [Sass](http://sass-lang.com/) and [Pug](https://pugjs.org/).

*Note: Weaverjs is simply a guideline and it doesn't solve everything. It is up to you to modify whatever necessary to achieve your project goals and dreams.*

## Table of Contents

1. [Quickstart](#quickstart)
1. [Directory Layout](#directory-layout)
1. [Build](#build)
    1. [Environments](#environments)
        1. [Development](#development)
        1. [Stage](#stage)
        1. [Production](#production)
1. [Server](#server)
    1. [Local URLs](#local-urls)
    1. [Options](#options)
1. [Deploy](#deploy)
    1. [Github Pages](#github-pages)
1. [Assets](#assets)
    1. [Fonts](#fonts)
    1. [Images](#images)
    1. [Media](#media)
    1. [Miscellaneous](#miscellaneous)
    1. [Vendors](#vendors)
      1. [Jquery example](#jquery-example)
1. [Scripts](#scripts)
1. [Styles](#styles)
    1. [iotaCSS](#iotacss)
1. [Views](#views)
    1. [Pug Structure](#pug-structure)
    1. [Environment Variables](#environment-variables)
1. [Contributing](#contributing)
1. [Inspiration](#inspiration)

## Quickstart

```
npm cache clear && npm i && npm run gulp
```

*Note: Before you can install packages, you will need to install [Node](https://nodejs.org/) and [NPM](https://www.npmjs.com/). It 's recommanded to use [nodenv](https://github.com/nodenv/nodenv) to manage them*

## Directory Layout

```
├── /dist/                        # The compiled output (generated by Gulp)
├── /src/                         # Application source files
│   ├── fonts/                    # Asset folder for fonts
│   ├── images/                   # Asset folder for images (jpg, png, ...)
│   ├── media/                    # Asset folder for media (mp4, webm, ...)
│   ├── misc/                     # Miscellaneous files for the root folder (favicon.ico, robots.txt, ...)
│   │   ├── all/                  # Miscellaneous files for all environments
│   │   ├── development/          # Miscellaneous files for development only
│   │   ├── production/           # Miscellaneous files for production only
│   │   └── staging/              # Miscellaneous files for staging only
│   ├── scripts/                  # Javascripts files
│   │   ├── components/           # Javascripts components files to be included
│   │   └── main.js               # Main Javascripts files
│   ├── styles/                   # Scss styles files
│   │   ├── base/                 # Base styles are the default styles of base elements.
│   │   ├── components/           # UI elements
│   │   ├── objects/              # Class-based selectors which define undecorated design patterns
│   │   ├── settings/             # Setting files contain global configurations that are shared by more than one modules
│   │   ├── tools/                # Specific style for each views
│   │   ├── utilities/            # High-specificity explicit classes
│   │   └── main.scss             # Global scss style file
│   ├── svg/                      # Asset folder for svg files
│   ├── vendors/                  # Vendors Javascripts files (jquery, ...)
│   │   ├── bundle.js             # Not minimized vendors Javascripts files (for development)
│   │   └── bundle.min.js         # Minimized vendors Javascripts files
│   └── views/                    # Pug included files
│       ├── extends/              # Pug view files
│       ├── includes/             # Pug reusable components
│       ├── mixins/               # Sets of pug mixins and functions.
│       └── site/                 # Pug view files
├── .node-version                 # Specific node version for nodenv
├── gulpfile.js                   # Gulp configuration
└── package.json                  # Project dependencies
```

## Build

```
npm run build
```

Generate a fresh build of your project. Task will run several individual tasks on files within `./src` and then output them to `./dist`.

### Environments

You can specify which environment you want to build. Development environment is used by default when building without option.

#### Development

```
npm run dev
```

#### Stage

```
npm run stg
```

#### Production

```
npm run prd
```

## Server

Start a local dev server with. Additionally, gulp will watch for any changes to files and reload browser while server is running.

```
npm run gulp server
```

## Deploy


### Github Pages

If you want to host your site on [Github Pages](https://pages.github.com), you can deploy directly a production version on the `gh-pages` branch. Therefore, you have to already commit once your project on a Github repository.

```
npm run github
```

### Local URLs

* Local - http://localhost:3000
* UI - Set to `false` by default

### Options

You can modify port, proxy, and many other settings in `./gulpfile.babel.js`. For more information about BrowserSync go to [http://www.browsersync.io/](http://www.browsersync.io/).

## Assets

Run several individual tasks to copy static files from `./src` to `./dist`.

```
npm run gulp assets
```

### Fonts

Copy font files to `./dist/fonts`.

```
npm run gulp fonts
```

### Images

```
npm run gulp images
```

Copy images to `./dist/images`. As a personal preference Weaverjs doesn't use automated image optimization. It is strongly recommended to use services like [TinyPNG](https://tinypng.com/) and [TinyJPG](https://tinyjpg.com/) to optimize images manually.

### Media

```
npm run gulp media
```

Copy media files to `./dist/media`.

### Miscellaneous

Copy miscellaneous files, such as `.htaccess` or `robots.txt`, to the root of `./dist`. If your project require custom settings per environment, then you can save individual files into appropriate directory within `./src/misc`.

```
npm run gulp misc
```

### Vendors

```
npm run gulp vendors
```

Bundle vendor files to `./dist/vendors`. You can install new client-side vendors using npm, then reference appropriate files in `./src/vendors/bundle.js` and `./src/vendors/bundle.min.js`.

#### Jquery example

Add jquery package in `package.json`
```javascript
"dependencies": {
  ...
  "jquery": "^x.x.x",
  ...
}

```

Reference it for development in `./src/vendors/bundle.js`
```javascript
// =include jquery/dist/jquery.js
```

And for minified version in  `./src/vendors/bundle.min.js`
```javascript
// =include jquery/dist/jquery.min.js
```


## Scripts

```
npm run gulp scripts
```

Run a series of sub-tasks to generate final JavaScript files.

*Note: Each file on the root of `./src/scripts` will be compiled to its own file in `./dist/scripts`. Each file can have own includes, just like Sass with `@import` functionality. See `./src/scripts/main.js` as an example.*

## Styles

```
npm run gulp styles
```

Run a series of sub-tasks to generate final CSS files. See `./gulpfile.babel.js` for reference.

*Note: Each file on the root of `./src/styles` will be compiled to its own file in `./dist/styles`.*

### iotaCSS

Weaverjs use [iotaCSS](https://www.iotacss.com) SASS based OOCSS framework built for scale.

## Views

```
npm run gulp views
```

Run a series of sub-tasks to generate final HTML files. See `./gulpfile.babel.js` for reference.

### Pug Structure

Weaverjs follows an opinionated directory structure. To learn more about Pug go to [https://pugjs.org/api/getting-started.html/](https://pugjs.org/api/getting-started.html/).

### Environment Variables

Every Pug file has access to global `env` variable. You can use it to conditionally load unminified/minified assets. See `./src/views/includes/head.pug` as an example.

### Contributing

1. Create a personal fork of the project on Github.
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

### Inspiration

Weaverjs is inspired by [web-starter-kit-gulp](https://github.com/KrisOlszewski/web-starter-kit-gulp) by @KrisOlszewski
