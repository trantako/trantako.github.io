# trantako.github.io

## About

This is a repository for GitHub Pages site for my personal account. The repository contains the files that are needed for generating my personal website. The generated website appears as https://tapani.rantakokko.net and is hosted here in GitHub via GitHub Pages.

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

For local development/testing I use local installation of Jekyll. Since it is not available for Windows, I use WSL a.k.a *Windows Subsystem for Linux*. In practice, there is Ubuntu 18.04 console inside Windows. This is enough and much more light-weight than installing the whole Ubuntu Linux as virtual machine.

### Steps to install Ubuntu 18.04 inside Windows 10

> When I did this, Ubuntu 20.04 had just come out. I tried to use it, but necessary packages were not available for it yet. I had to install also 18.04 and use that instead.

1. In Windows taskbar search box, type “powershell,” right-click it from the search results, and select “Run as administrator”.

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

> I had problems when intalling Jekyll without 'sudo'. See [this](https://jekyllrb.com/docs/troubleshooting/#no-sudo) for instructions. This info did not solve everything; I had to re-install Ruby etc. tricks before I got it working. It took several hours of problem solving. Much easier to use native Ubuntu or Mac for running Jekyll!

## Testing

Use the local Jekyll installation for testing the changes before deployment to GitHub (the changes will go live immediately when pushed there).

1. Open Ubuntu console, or open command prompt and type:
```
bash
```

2. Go to correct directory:
```
cd Development/VCS/github/trk/trantako.github.io/
```

3. Start serving the site locally with Jekyll:
```
bundle exec jekyll serve
```

4. Open Chrome browser and navigate to [localhost:4000](localhost:4000).

5. Once done, CTRL-C in Bash to stop Jekyll.

## Deployment

Just commit and push the changes to this repository. GitHub will automatically update the site!

## Troubleshooting

Check the discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll). Other resources:

- [Ruby 101](https://jekyllrb.com/docs/ruby-101/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Configuring GitHub Metadata](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) to work properly when developing locally and avoid `No GitHub API authentication could be found. Some fields may be missing or have incorrect data.` warnings.
