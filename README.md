# ResBaz Auckland Template
* Based on: Project Zeppelin / GDG DevFest 2014 site template

## Instructions for ResBaz Site Editors

### Blog Posts
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

### Home page sections
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

### Sessions Page
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

### Speakers Page
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

### Schedule Page
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
* **Note 2: There are two items in `_data/sessions.yml` which are used to specify lunch/coffee breaks, by default these have the IDs `503` and `307` respectively.
* The example above shows a single day with 4 'tracks/streams'. In the timeslot from `11-11:45` there would be no talks for `Stream 1-3`, and the item with the ID `001` specified in `_data/sessions.yml` would appear in `Stream 4`.


---

## Zeppelin Template Instructions Follow

### About
Project Zeppelin allows you to setup awesome GDG DevFest site in 5 minutes.

Project is built on top of [Jekyll](http://jekyllrb.com/) - simple, blog-aware, static site generator. Jekyll also happens to be the engine behind GitHub Pages, which means you can use Jekyll to host your website from GitHub’s servers for free. [Learn more about Jekyll](http://jekyllrb.com/).

Template is brought by [GDG Lviv](http://lviv.gdg.org.ua/) team.

### Live demo http://gdg-x.github.io/zeppelin/

#### Automated version with Grunt <https://github.com/gdg-x/zeppelin-grunt>

### Features
* Easy to setup
* Simple and responsive design
* Integrated speakers and sessions management
* SVG icons
* SEO friendly


### Quick-start guide
1. [Fork](https://github.com/gdg-x/zeppelin/fork) this repo
2. Clone locally
3. Update ```_config.yml```
4. Select what content blocks do you need
5. Push changes to ```gh-pages``` branch
6. Enjoy your awesome DevFest site at ```http://[your github name].github.io/zeppelin/```

Or watch project presentation from [GDG[x] Townhall meeting](http://www.youtube.com/watch?v=xYmhheoLjcI). Slides available [here](https://docs.google.com/presentation/d/19aM7yNl_orDaCNND5LpCY3fShb6PyMltnzYfKvV8R_8/edit?usp=sharing)


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
Site will be available at http://127.0.0.1:4000/zeppelin/ or http://localhost:4000/zeppelin/ (on Windows)

**NOTE:** in this mode all changes to html and data files will be automatically regenerated, but after changing ```_config.yml``` you have to restart server.

### Sass(Compass) support
**Note:** You need to install [Node.js](http://nodejs.org/download/)

To watch changes of `.sass` files and compile it to the `.css` on a fly change property `safe: true` to `safe: false` in `_config.yml`.
**Note: It works only on local machine, because GitHub runs Jekyll in `--save` [mode](https://help.github.com/articles/using-jekyll-with-pages/#configuration-overrides)**

Learn more about Sass development from [documentation](https://github.com/gdg-x/zeppelin/wiki/Sass-development).


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

Learn more about available optimization options from [documentation](https://github.com/gdg-x/zeppelin/wiki/Resources-optimizations).

### Documentation
Quick-start guide is not enough? Checkout [full documentation](https://github.com/gdg-x/zeppelin/wiki).

### Used libraries
* [Bootstrap](https://github.com/twbs/bootstrap)
* [Animate.css](https://github.com/daneden/animate.css)
* [Waves](https://github.com/publicis-indonesia/Waves)
* [jquery.appear](https://github.com/bas2k/jquery.appear)
* [jQuery countTo Plugin](https://github.com/mhuggins/jquery-countTo)
* [Typed.js](https://github.com/mattboldt/typed.js)
* [Sticky-kit](https://github.com/leafo/sticky-kit)

### Who is using template?
Going to use template? Go on! The only thing we ask - let us know at [*lviv@gdg.org.ua*](mailto:lviv@gdg.org.ua) so we can include you to this list, or make a pull request.

| | | |
|------|------|------|
| [GDG DevFest Ukraine 2014](http://devfest.gdg.org.ua/) | [GDG DevFest Istanbul 2014](http://2014.devfesttr.com/) | [GDG Bangalore Site](http://gdgbangalore.github.io/) |
| [GDG DevFest Omsk 2014](http://gdg-devfest-omsk.org/) | [2014 南阳 GDG Devfest 大会](http://devfest.gdgny.org) | [DevFest Nordeste 2014](http://2014.devfestne.com.br/) |
| [GDG DevFest The Netherlands](http://www.devfest.nl/) | [DevFest Centro-Oeste 2014](http://www.devfestcentrooeste.com.br/) | [Android DevFest Space Coast](http://gdg-space-coast.github.io/zeppelin/) |
| [DevFest SP 2014](http://sp.devfest.com.br/) | [DevFest in Baroda](http://devfest.gdgbaroda.com/) | [GDG Hi Pic (France)](http://maximemularz.github.io/zeppelin/) |
| [GDG DevFest Córdoba 2014](http://gdgcordoba.github.io/zeppelin/) | [GDG DevFest Düsseldorf 2014](http://www.gdg-dus.de/DevFest2014/) | [GDG Makerere DevFest 2014](http://gdgmakerere.github.io/) |
| [GDG Dublin DevFest 2014](http://gdg-dublin.appspot.com/) | [GDG Busitema DevFest 2014](http://gdgbusitema.github.io/) | [DevFest Vienna 2014](http://www.devfest.at/) |
| [Android Wear DevFest](http://devfest.gdgnorthjersey.com/wear2014/) | [GDG SLAU DevFest 2014](http://gdgslau.github.io/) | [Lima DevFest](http://limadevfest.com/) |
| [GDG Korea DevFair 2014](http://devfair2014.gdg.kr/) | [GDG DevFest Kota Kinabalu 2014](http://devfest.gdgkk.info/) | [GDG DevFest Belgium](http://gdg-brussels.org/DevFest2014/) |
| [DevFest Praha 2014](http://devfest.cz/) | [GDG DevFest Kosice](http://devfest.sk/) | [GDG DevFest Cagayan de Oro](http://devfest.gdgcdo.org/) |
| [DevFest Birgunj](http://gdgbirgunj.github.io/DevFest2014/) | [GDG DevFest Poland](http://devfest.pl/) | [GDG DevFest Silicon Valley](http://devfest2014.gdgsv.com/) |
| [DevFest Chennai 2014](http://devfest.gdgchennai.com/) | [GDG DevFest Bari](http://gdgbari.github.io/zeppelin/) | [GDG DevFest Ahmedabad](http://devfest.gdgahmedabad.com/) |
| [GDG DevFest Sri Lanka](http://www.devfestlk.org/) | [GDG DevFest Tunis](http://devfest.gdgtunis.org/) | [GDG DevFest Kozhikode](http://devfest.gdgkozhikode.org/) |
| [GDG DevFest Argentina](http://devfest.gdg.com.ar/) | [GDG DevFest Bhubaneswar](http://devfest2014.gdgbbsr.com/) | [GDG DevFest Miage Gi](http://gdgmiagegilab.github.io/) |
| [GDG DevFest NORTE](http://norte.devfest.com.br/) | [GDG Devfest Nyeri 2014](http://devfest.gdgkimathiuniversity.com/) | [GDG DevFest Paris](http://devfest.gdgparis.com/) |
| [GDG Akure](http://gdgakure.github.io/)|[MENAT GDG Summit 2014](http://summit.gdg-menat.com/)|[Women Techmakers Istanbul 2015](http://2015.wtmistanbul.com) |
| [GDG DevFest Mallorca](http://devfest.gdgmallorca.com/)| [Michigan GDG DevFest 2015](http://michigandevfest.com/) | [International Women's Day](http://iwd.gdgnorthjersey.com/womeninnovation/) |
| [Women Techmakers Tbilisi 2015](http://womentechmakers.ge/) | [Android Xtended](http://www.androidxtended.com/) |[GDG Bingham University](http://binghamuni.edu.ng/gdg)|
| [JSday Maceio 2015](http://jsday.com.br) | [DevFest Nordeste 2015](http://2015.devfestne.com.br) | [GDG DevFest Vijayawada 2015](http://devfest.gdg-vijayawada.org) |
| [Geek Night Recife](http://geeknightrecife.github.io/) | [IO Extended 2016 Madrid ](http://io.gdg.es/) | [AngularCamp](http://angularcamp.org/) |
| [Mobile Era 2016](http://mobileera.rocks/) | [GDG Francisco Beltrão](http://gdg-fb.github.io) | [Women Techmakers Istanbul 2016](http://2016.wtmistanbul.com) |
| [Droidcon Paris 2015](http://droidcon.fr) | [Android Makers Paris 2017](http://androidmakers.fr) | [Heidelberger Symposium 2017](https://heidelberger-symposium.de/) |
| [DevFest Foumban website](http://devfestfoumban.org) | [NorthSec 2018](https://nsec.io/) | [SwiftFest 2018](http://swiftfest.io) |
|[LASCAR Workshop](http://lascar.sda.tech/)| [Core C++ 2019](https://corecpp.org/) ||


### Contributors
* Design and web development: [Oleh Zasadnyy](https://github.com/ozasadnyy)
* Idea: [Vitaliy Zasadnyy](https://github.com/zasadnyy)

See [list of contributors](https://github.com/gdg-x/zepplin/graphs/contributors)

Maintainers: [@tasomaniac](https://github.com/tasomaniac) and [@ozasadnyy](https://github.com/ozasadnyy).

### License
Project is published under the [MIT license](https://github.com/gdg-x/zeppelin/blob/master/LICENSE.txt). Feel free to clone and modify repo as you want, but don't forget to add reference to authors :)
