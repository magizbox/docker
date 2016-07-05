# Web

# Receipts:

UI: jqueyr, bootstrap
Helper: underscore, sprintf, moment
Framework: angularjs

### Installation

Step 1.1: Install all needed dependencies

[code lang="bash"]
bower init
```

Add dependencies to `dependencies` in `bower.json` file

```
    "jquery": "~2.2.3",
    "underscore": "~1.8.3",
    "moment": "~2.13.0",
    "sprintf": "~1.0.3",
    "angularjs": "~1.5.5",
    "bootstrap": "~3.3.6"
```

Install dependencies

```
bower install
```

Change `index.html` file

[code lang="html"]
<script src="./bower_components/jquery/dist/jquery.min.js"></script>
<script src="./bower_components/bootstrap/dist/js/bootstrap.js"></script>
<script src="./bower_components/sprintf/dist/sprintf.min.js"></script>
<script src="./bower_components/underscore/underscore.js"></script>
```


### Fast HTML Typing

[Zen Coding](https://www.smashingmagazine.com/2009/11/zen-coding-a-new-way-to-write-html-code/)

# Web: Docker

Image

[httpd](https://hub.docker.com/_/httpd/)

Dockerfile

```
FROM httpd:2.4

COPY ./app/ /usr/local/apache2/htdocs/
```

Compose

```
ui:
 build: ./ui-app/.
 links:
  - service
 ports:
  - 80:80
```

