# hexo-intuitive-image
A better and intuitive way to store and use images alongside your post:
- place image anywhere you want, use it with normal markdown image syntax
- provide cdn for your images([Powered by jsDelivr](https://www.jsdelivr.com/features)) if your blog is served from github pages

## Why
Why not use hexo builtin [Asset Folders](https://hexo.io/docs/asset-folders) ?

My original request: I customize `new_post_name` to `:year/:title/index.md`, I want to store any related images inside the folder `:title`, and use images in an intuitive way, so that I can change my post title with no cost.

`Asset Folders` won't work out for two reasons:
1. It's not friendly for none English users: I'm speaking Chinese but I don't like encoded codes in any uri path
2. It won't working if you customize `new_post_name` instead of the default value. 

## How to use
### Install
with yarn

```sh
yarn add hexo-intuitive-image -D
```

with npm

```sh
npm install hexo-intuitive-image -D
```

### Writing post
use local images by intuitive way:  
> you can refer any image from your post, the image path should be relative to your post.
>   there is no folder naming or structure requirements, refer an image at your will

for example:
1. you got a post in path `source/_posts/2021/tips-for-google-search/index.md`
2. and you have an image in `source/_posts/2021/vue-vs-react/vue.png`
3. you can use image `vue.png` from the post in following syntax:
   `![vue logo](../vue-vs-react/vue.png)`

### Config
you may add following config to hexo's config `_config.yml` to enable more features:
```yml
intuitive_image:
  # set to true to rename image name with its hash instead of its original name
  #   to avoid naming conflicts(different images with same names) and file duplications(same images with different names)
  hash: true
  # enable cdn powered by jsdelivr.com
  cdn:
    # github repo path: <github-username>/<github-repo-name>
    repo: oe/blog.evecalm.com
    # branch that served github pages
    #   leave it empty will use the default branch(normally `master` or `main`)
    branch: gh-pages
```

## FAQ
1. What's the final path of the images?
  > images will be under the same folder with the post's published path. e.g.:
  >   1. post path is `/2021/archived/tips-for-google-search.html`, images of it will be in path `/2021/image-assets/`
  >   2. post path is `/tips-for-google-search.html`, images of it will be in path `/image-assets/`
2. (no more questions in my mind😄

If you got any questions or feature requests, feel free to [create an issue](https://github.com/oe/hexo-intuitive-image/issues/new).