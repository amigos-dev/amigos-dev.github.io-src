# Amigos Development Corporation


## Initializing

Repository uses submodules for themes, cloned under themes subdirectory. 
To clone:
```
 git clone --recursive git@github.com:amigos-dev/amigos-dev.github.io.git
```


## Usage

In order to see your site in action, run Hugo's built-in local server.

```
# Update themes submodules - optional state to pick up theme changes, rarely performed step
$ git submodule init
$ git submodule update

$ hugo server -w -D
```

Now enter [`localhost:1313`](http://localhost:1313) in the address bar of your browser.
Note that if an alternative listening port is desired, you can start hugo server with -p switch. 

For more information check out the official [Hugo documentation](http://gohugo.io/overview/usage/).


## Adding new content

### Blog posts

Theme blog template will pick up all Markdown (.md) files in subtree content/blog, but it is important for all these files to have a front matter block. To get it done correctly use Hugo new command, for example:
```
hugo new content/blog/2022-07-05-going-live.md
```

Desired, but not required, naming convention is to use date as a prefix to allow for easier by-name sorting when number of posts grows. 

### Modifying home page

Home page layout is described in HTML template (see https://gohugo.io/templates/homepage/), located in layouts/index.html, it includes the text block from content/_index.md, which is expected to be edited more frequently. 

## License

This web site is released under the MIT License. 
