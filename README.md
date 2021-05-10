# 🔗 URL Shortener 

**Hosted by Github Pages**

This is a minimal URL shortener that can be entirely hosted on GitHub pages. It does not need the maintenance of any servers or databases and can be hosted
entirely on GitHub for free! This repo is forked from [nelsontky/gh-pages-url-shortener](https://github.com/nelsontky/gh-pages-url-shortener) and maintained.

**Link to Repo:** [fluted.xyz/s/1](https://fluted.xyz/s/1)

## Usage

To add a new link: 
- Open an issue **with the title being the link you want to shorten** including the `http(s)://` to [/s/issues](https://github.com/fluteds/s/issues). 
   - Note: Closed issues also work with this URL shortener.
- The newly created short url can be accessed via the users default GitHub pages domain or a custom domain (if enabled.)
   - Note: There is no need to put the pound symbol as the URLs look like this: `website.xyz/s/1` instead of this: `website.xyz/s/#1`.

## Features

Unlike many URL shorteners, this one uses a "database" in the form of GitHub issues and can be entirely hosted via GitHub pages. 


## How can I use this with my own domain?

Disclaimer: This method of creating a URL shortener is hacky and not meant to
be reliable. It may break or be patched at anytime. Proceed at your own risk!

1. Fork the repo.
2. Set up GitHub pages for your **forked** repo.
   1. In your **forked** repo, **click the Settings tab** and scroll down to the GitHub Page section.
   2. Then select the **main branch** source and click on the **Save** button.

  ![How to Create a GitHub Page for Your Repo](https://i.imgur.com/kjinFX9.png)

### If you are using your own domain

   1. [Set your domain up for GitHub pages.](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
   2. Change the URL in `CNAME` file to your domain.
   3. Push your changes to your database/forked repo.

### If you are using GitHub's default domain

It looks something like `https://<username>.github.io/<repo-name>/`

1. Delete the `CNAME` file.
2. Change `var PATH_SEGMENTS_TO_SKIP = 0;` at the top of `404.html` to `var PATH_SEGMENTS_TO_SKIP = 1;`. This is because GitHub domains have an additional path segment (the reponame) after the host name.
3. (Optional) Create a new repo or use your forked repo as a database.
4. Update `var GITHUB_ISSUES_LINK = "<your-github-issues-link>";` at the top of `404.html` accordingly afterwards.
5. Format for `GITHUB_ISSUES_LINK`: `https://api.github.com/repos/{owner}/{repo}/issues/` Remember to put the trailing `/`!
6. Push your changes to your database/forked repo, and your low cost and cool as heck URL shortener will be ready for use!
