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

## Testing 

### Testing locally

`hugo server -D -w` access from the browser as localhost:1313
`hugo server -D -w -p 1314` access from the browser on a non default port as localhost:1314

### Staging 

Default staging github action publishes from the branch staging into repository test.amigos-dev.github.io, accessible from the custom domain amigosdev.com. Publishing is triggered by push into staging branch

### Create github pages site for buddy demonstration before 

Separate repository allows manual publishing of the site for demonstrating, repository name is : amigos-dev/buddytest and it is published as https://amigos.dev/buddytest/ . It contains subdirectories per user, each contains a replica of a published web site, so your replica of the web site will be accessed as https://amigos.dev/buddytest/vlads 

To publish into your subdirectory, assuming current directory is a clone of amigos-dev.github.io-src use following sequence as a example

`
#Checkout your development branch
git checkout vlads-dev

#Publish into the clone of buddytest, assuming it is located as a peer project clone
#Update buddytest repo first
pushd ../buddytest && git pull --rebase && popd
rm -fr ../buddytest/vlads/*
#Publish into per user subdirectory
hugo -D -d ../buddytest/vlads
#push back
pushd ../buddytest && git commit -am "Update from vlads" && git push && popd

## License

This web site is released under the MIT License. 
