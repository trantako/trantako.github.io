# trantako.github.io

## About

This is a repository for the GitHub Pages site for my personal account. The repository contains the files that are needed for generating my personal website. The generated website appears as https://tapani.rantakokko.net and is hosted here in GitHub via GitHub Pages.

## Framework

The website is generated from Markdown texts, images, and other source files using [Jekyll](https://jekyllrb.com/). The look & feel is based on the [Minimal Mistakes Jekyll theme](https://github.com/mmistakes/minimal-mistakes).

Both the project files and content files reside in this repository's master branch, from which GitHub will pick it up and generate the GitHub Pages site.

## Development Tools

Current setup for maintaining the site:
- Windows 10 desktop computer at home
- Visual Studio Code as an IDE for writing content and editing project files
- Version control via GitHub
- Site hosting via GitHub Pages
- Custom domain name via Louhi
- Chrome browser for testing/viewing the site

For local development/testing I use a local installation of Jekyll. Since it is not available for Windows, I use WSL a.k.a *Windows Subsystem for Linux*. In practice, there is Ubuntu 18.04 console inside Windows. This is enough and much more light-weight than installing the whole Ubuntu Linux as a virtual machine. When I want to develop the website locally, I do this:

Open Windows command prompt and type this:
```
C:\Users\trk>bash
trk@Veronica:/mnt/c/Users/trk$ cd Development/VCS/github/trk/trantako.github.io/
trk@Veronica:/mnt/c/Users/trk/Development/VCS/github/trk/trantako.github.io$ bundle exec jekyll serve --livereload
```

### Steps to install Ubuntu 18.04 inside Windows 10

> When I did this, Ubuntu 20.04 had just come out. I tried to use it, but the necessary packages were not available for it yet. I had to install also 18.04 and use that instead.

1. In the Windows taskbar search box, type “Powershell,” right-click it from the search results, and select “Run as administrator”.

2. Enter the following command:

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

3. Restart the computer (this *must* be done now).

4. Open Microsoft Store e.g. via Windows taskbar search box, find Ubuntu 18.04 from the store, and install it.

5. After installing has completed, start it. The first time it takes a while to initialize. Create a user account. Update Ubuntu by typing the following commands in bash:

```
sudo apt-get update
sudo apt-get upgrade
```

### Steps to install Jekyll via Bash (Ubuntu 18.04) on Windows 10

1. Open Ubuntu console, or open command prompt and type:
```
bash
```

2. To install Ruby (programming language of Jekyll), add BrightBox repo. Then update apt and install packages for Ruby:
```
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
```

3. Update Ruby gems:
```
gem update
```

4. Install Jekyll:
```
gem install jekyll bundler
```

> Note: No 'sudo' here.

5. Test Jekyll:
```
> jekyll -v
jekyll 4.0.0
```

> I had problems when installing Jekyll without 'sudo'. See [this](https://jekyllrb.com/docs/troubleshooting/#no-sudo) for instructions. This info did not solve everything; I had to re-install Ruby etc. tricks before I got it working. It took several hours of problem-solving. Much easier to use native Ubuntu or Mac for running Jekyll!

## Testing

Use the local Jekyll installation for testing the changes before deployment to GitHub (the changes will go live immediately when pushed there).

1. Open Ubuntu console, or open command prompt and type:
```
bash
```

2. Go to the correct directory:
```
cd Development/VCS/github/trk/trantako.github.io/
```

3. Start serving the site locally with Jekyll:
```
bundle exec jekyll serve --livereload
```

4. Open Chrome browser and navigate to [localhost:4000](localhost:4000).

5. Once done, CTRL-C in Bash to stop Jekyll.

## Deployment

Building the site locally:
```
bundle exec jekyll build
```

> Notice that it is enough for deployment to just commit and push the changes to this repository. GitHub will automatically update the site. No need to do the build step.

## Updating & customization

There are many strategies in getting updates to the theme. To keep this as hassle-free as possible (focus on content, not on the framework), I have chosen to use a remote theme approach: the theme comes from its own public repository. Specific tag/branch can be selected (fixed) if necessary, but currently it is not specified ie. I use the latest version, whatever it is.

To customize things that cannot be configured, the solution is to create local customization files. See the theme [structure](https://mmistakes.github.io/minimal-mistakes/docs/structure/).

## 3rd party components

Before-after image slider: [twenty-twenty](https://github.com/zurb/twentytwenty)

1. In frontmatter, select a custom layout:
```
layout: drawing
```

2. In markdown, use like this:
```
<br />
<div id="imageSliderHor1" class='twentytwenty-container'>
  <img src="/assets/images/drawing/tiina_scanned.jpg" style="transition: none; webkit-transition: none">
  <img src="/assets/images/drawing/tiina_edited.jpg" style="transition: none; webkit-transition: none">
</div>

*"Tiina". Pencil on paper, 2015.* 
{: style="text-align: center;"}
```

> Style transition needs to be disabled as shown above, else transitions are applied to sliding.

> In _layouts, you'll find a custom layout *drawing.html* that loads and configures javascript for the slider.

The way to initialize the plugin according to instructions does not work in markdown:
```
<script>
$(function(){
  $("#container1").twentytwenty();
});
</script>
```

This results to invisible slider and an error in Chrome developer tools:
```
jquery-3.2.1.min.js:2 Uncaught TypeError: $(...).twentytwenty is not a function
    at HTMLDocument.<anonymous> (VM257 heidi:314)
    at j (jquery-3.2.1.min.js:2)
    at k (jquery-3.2.1.min.js:2)
```

The case seems a bit similar than this, although we are not dealing with Wordpress here:

> When you use WordPress’ built-in jQuery, it’s automatically loaded in noConflict mode, where the $ shortcut isn’t available. Usually, you can get around this by wrapping the JavaScript:
>
>```
>jQuery( document ).ready( function( $ ) {
>  // the $ shortcut is available within this function
>} );
>```



## Experiences

After using this setup for a couple of months, I am happy with it. Creating new content is efficient and everything is simple enough and works smoothly.

I use the theme's documentation site frequently to check out things:

[Minimal Mistakes theme docs](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

I have also managed to get Grammarly working with Visual Studio Code so that grammar is checked when I type. This was a bit complicated, but works pretty well now.

Hosting my website like this (via GitHub Pages) is free. The pages also load very quickly from GitHub's global CDN. Moreover, a static site is totally maintenance-free, and secure. 

However, a GitHub repository is not suitable for storing large media files. For media content, I have made the following choices:

- Photos: I upload most of the images to Google Photos, usually straight from my phone. Then, I create an album in Google Photos for a particular topic, add all images that I want to reference into that album, and then make it public. Now, I can get a direct image link for each individual photo. It helps in organizing to have a separate (public) album for each topic. Hosting images like this is free.

- Videos: I upload my videos to Youtube, either public or hidden, and then I use the iFrame method for embedding them on the web pages (HTML code directly into the markdown text files). Hosting videos like this is free.

- Music: I upload my audio tracks to SoundCloud, and embed their player using the iFrame method, similar to Youtube videos. Hosting audio like this is free.

GitHub Pages offers some basic analytics, but to really understand how the website is being used and what is the effect of, say, posting a link to an article via social media, I use Google Analytics.

## Troubleshooting

Check the discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll). Other resources:

- [Ruby 101](https://jekyllrb.com/docs/ruby-101/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Configuring GitHub Metadata](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) to work properly when developing locally and avoid `No GitHub API authentication could be found. Some fields may be missing or have incorrect data.` warnings.
