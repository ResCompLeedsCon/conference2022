# ResBaz Auckland Template
* This is a conference template created by Sam Kavanagh based largely on the Project Zeppelin / GDG DevFest 2014 site template.

### Features
* Easy to setup
* Simple and responsive design
* Integrated speakers and sessions management
* SVG icons
* SEO friendly

# Quick-start guide
1. Fork this repo
2. Clone locally
3. Update ```_config.yml```
4. Select what content blocks do you need
5. Push changes to ```gh-pages``` branch
6. Enjoy your awesome site at ```http://[your github name].github.io/```

**Note**: By default this template assumes you are going to be using a custom domain with it, and your files will be served from the root folder of this address. In order to deploy this site as a subdirectory, e.g. ```http://[your githubname].github.io/resbaz``` modify the `baseurl` field in `_config.yml` (in this example to `/resbaz`).

## Local development

Check if you have [all requirements for local environment](http://jekyllrb.com/docs/installation/).
To install all development dependencies install [Bundler](http://bundler.io/).
```bash
    gem install bundler
```
and run next command from root folder:

```bash
  bundle install
```  

To start Jekyll run:
```bash
    jekyll serve -w
```
Site will be available at http://127.0.0.1:4000/ or http://localhost:4000/ (on Windows)

**NOTE:** in this mode all changes to html and data files will be automatically regenerated, but after changing ```_config.yml``` you have to restart server.

### Sass(Compass) support
**Note:** You need to install [Node.js](http://nodejs.org/download/)

To watch changes of `.sass` files and compile it to the `.css` on a fly change property `safe: true` to `safe: false` in `_config.yml`.
**Note: It works only on local machine, because GitHub runs Jekyll in `--save` [mode](https://help.github.com/articles/using-jekyll-with-pages/#configuration-overrides)**

### Resource optimizations (optional)

You can optimize images and minify css and javascript automatically (for now only on Windows).
But for Mac OS users available amazing tool - [imageoptim](https://imageoptim.com/). Thanks [@raphaelsavina](https://github.com/raphaelsavina) for link.
Optimize all images by running this script from `/automation/images/` folder:
```bash
    all_image_optimization.bat -d -jtran -pout -pquant -optip -gsicle -svgo
```

To minify CSS and JS run `minify_js.bat` (for Windows) and `minify_js.sh` (for Linux and MacOS) from `/automation/minifying/` folder:
```bash
    minify_js.bat
```

Learn more about available optimization options from the original Zeppelin template's [documentation](https://github.com/gdg-x/zeppelin/wiki/Resources-optimizations).

# Instructions for ResBaz Site Editors

## Blog Posts
* All blog posts are located in the `_posts/` folder.
* New blog posts are created simply by creating a new file in this folder and following the naming convention `YYYY-MM-DD-title-here.markdown`
* All blog posts should begin with the following code snippet:

```
---
layout: post
title:  "Post title goes here!"
date:   2019-03-25 12:38:00
isStaticPost: false
---
Actual post content goes here. Note the date above should match the filename.
```

## Home page sections
* To **enable/disable** a content block on the homepage, simply add/delete on of the lines in the `index.html` file located in the root folder. E.g. to disable the 'Rockstar Speakers' block simply remove the line:

```
 {% include rockstar-speakers.html %}
```

* To **edit** the content of one of these sections find the corresponding section in the `_config.yml` file located in the root folder. E.g. to edit the 'About' block, edit the section:

```
# About Block
aboutTitle: "About ResBaz Auckland"
aboutSubtitle: "Conference"
aboutText: "<p>The Research Bazaar is a worldwide festival promoting the digital literacy emerging at the center of modern research. Throughout 2019, events will be held at a number of university campuses around the globe.</p>
```
* Note that when developing locally Jekyll needs to be restarted before any changes to `_config.yml` are visible.

## Sessions Page
* To **add/edit** the content that appears on either the 'Sessions' page, simply modify the file `_data/sessions.yml`.
* Note that this data is also used in other pages, e.g. the 'Schedule' page, and changes to content that already appears in the 'Schedule' page will also be reflected there. However for an item to appear in the schedule, it has to be referenced in the `_data/schedule.yml` file.
* Regardless of whether an item in `_data/sessions.yml` has been referenced in `_data/schedule.yml`, it will still appear in the 'Schedule' page.
* Insert new items in the following format:

```
-
  id: 007
  title: "Crash course in Pen Testing"
  description: "Learn the basics of pen testing. Martinis provided."
  subtype: workshop
  speakers: [4, 5, 6]
  complexity: "Beginner" 
  presentation: "https://link-to-any-resources.com/resource.pdf"
```
* Note that the `complexity`, `presentation`, and `subtype` fields are all optional.
* The `speakers` field references the ID of speakers, listed in the `_data/speakers.yml` file.

## Speakers Page
* To add/modify speakers, simply modify the file `_data/speakers.yml`.
* These appear in the format:

```
- 
  id: 4
  name: "Sam"
  surname: "Kavanagh"
  company: "Centre for eResearch"
  title: "eResearch Engagement Specialist"
  bio: "Sam is a member of the Centre for eResearch's engagement team and is teaching the LaTeX workshop."
  thumbnailUrl: "sam_kavanagh.jpg"
  rockstar: true
  ribbon:
    - {abbr: "CeR", title: "Centre for eResearch", url: "https://eresearch.auckland.ac.nz"}
  social: 
    - {name: "github", link: "https://github.com/Hganavak"}
```
* Note the `rockstar` field determines whether a speaker appears in the `Rockstar Speakers` block on the homepage
* The `thumbnailURL`, `ribbon`, and `social` fields are all optional

## Schedule Page
* To make updates the schedule, simply modify the file `_data/schedule.yml`.
* Days are each specified separately, and can have their own start/end times, timeslots, and streams.
* These appear in the following format:

```
- 
  date: "2019-07-10"
  dateReadable: "July 10"
  tracks: 
    - {title: "Stream 1", color: "#90be4e"}
    - {title: "Stream 2", color: "#03a9f4"}
    - {title: "Stream 3", color: "#e91e63"}
    - {title: "Stream 4", color: "#FF00FF"}
  timeslots:
    - {
    	startTime: "10:00",
    	endTime: "10:45",
    	sessionIds: [002, 404, 002, 001]
    }
    - {
        startTime: "11:00",
        endTime: "11:45",
        sessionIds: [404, 404, 404, 001]
    }
    - {
    	startTime: "12:00",
    	endTime: "11:45",
    	sessionIds: [307]
    }
- 
```
* **Note 1: A session id of `404` is used to specify that there is nothing on in this timeslot**.
* **Note 2: There are two items in `_data/sessions.yml` which are used to specify lunch/coffee breaks, by default these have the IDs `503` and `307` respectively.**
* The example above shows a single day with 4 'tracks/streams'. In the timeslot from `11-11:45` there would be no talks for `Stream 1-3`, and the item with the ID `001` specified in `_data/sessions.yml` would appear in `Stream 4`.

---

### Live demo https://resbaz.auckland.ac.nz/

### Used libraries
* [Bootstrap](https://github.com/twbs/bootstrap)
* [Animate.css](https://github.com/daneden/animate.css)
* [Waves](https://github.com/publicis-indonesia/Waves)
* [jquery.appear](https://github.com/bas2k/jquery.appear)
* [jQuery countTo Plugin](https://github.com/mhuggins/jquery-countTo)
* [Typed.js](https://github.com/mattboldt/typed.js)
* [Sticky-kit](https://github.com/leafo/sticky-kit)
* [Masonry](https://masonry.desandro.com/)

### License
Project is published under the MIT license. Feel free to clone and modify repo as you want, but don't forget to add reference to authors.

The original creators of the Zeppelin template also ask that you [contact them](lviv@gdg.org.ua) when your site is live as they maintain a gallery/list of their template instances.
