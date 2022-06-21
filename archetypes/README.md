# This is my blog repo

## Description

This repo is buily by this post.

[Create a Free Blog Site Using GitHub Pages and Hugo](https://youngkin.github.io/post/createafreeblogsite/)

## Manual

### Create a new post

```
# or any other folder name instead of "post"
hugo new post/<post filename>.md
```

After finishing writing the article, it's important to modify ```draft``` property to false, otherwise the post won't show on blog by default.

### Deployment

Deployment to GitHub page is executed by following shell batch file.

```
./deploy.sh
```