# Notes

Notes on the development of Golob.

### What it should do:

* Take a directory of markdown files and build a static blog. 

### HTML Templates

Golob will include a basic bootstrap layout with a navbar and content container.

The majority of work will be generating the blogpage containing the posts. 

### Golob syntax:

Golob uses its own syntax to define routing for your static site.

My current site is something like:

Header -> {Posts->index, Projects->projects, About Me->about, Resume->resume}

So, Header is the header navbar and each antecedent in the block of the consequent of the header is an element of the Header.

The consequent for Posts, index, is a reserved word in Golob for the page containing all of the posts. 

The other consequents must have a corresponding markdown file for that URL to point to. 

So, the source folder would look like:

source/
    _posts/
    _pages/
    _resources/
    golob_config.json

The _posts directory contains markdown files. For details on how to format these posts, see the Post Syntax section. 

The _pages directory contains markdown or HTML files of other pages like About Me or Projects which you would like to link to from your blog. HTML files will be unchanged.

The _resources directory contains assets like images and pdfs which are used in your posts. This may not end up being used.

The config file `golob_config.json` is where you can define the golob syntax expression for your site, as well as some other stuff probably.

### Mechanics:

Jekyll uses liquid as a templating engine. So, you need to write HTML pages with liquid syntax so Jekyll knows where to put the content. This seems tedious, so we will give golob default pages. 

### Markdown/Post Syntax:

Jekyll uses a specific date format as the beginning of the file name for each post. Golob does not require this, instead moving the date in with the rest of the posts' metadata.

Jekyll uses YAML "front matter" on the markdown posts for information regarding layout, title, etc. Posts in golob have an assoicated metadata file with the format:

`post-name-meta.json`

If no metadata json file is present, the post(s) will not be included. 
