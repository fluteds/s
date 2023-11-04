# 🔗 URL Shortener

This is a minimal URL shortener that can be entirely hosted on GitHub pages. It does not need the maintenance of any servers or databases and can be hosted
entirely on GitHub for free! This repo is forked from [nelsontky/gh-pages-url-shortener.](https://github.com/nelsontky/gh-pages-url-shortener)

## Usage

To add a new link:

- Open an issue with the title being the link you want to shorten including the `http(s)://` to [/sdb/issues.](https://github.com/fluteds/sdb/issues)
  
Closed issues also work with this URL shortener. The newly created short url can be accessed via the users default GitHub pages domain or a custom domain (if enabled.)

## URL Formatting

- URLs are formatted as the following: `website.xyz/1`
- URLs that are formatted as `website.xyz/s/#1` with the hash symbol are not valid and will 404.
- Adding a `?` at the end of a search does not redirect and shows the unshortened URL eg. `website.xyz/1?`
- Searching `website.xyz/{TEXT}` rather than `website.xyz/{NUMBER}`, will attempt to match and redirect to `website.xyz/{TEXT}` if an issue has the queried text as its description.

## Features

Unlike many URL shorteners, this one uses a "database" in the form of GitHub issues and can be entirely hosted via GitHub pages. The downside to it is that shortened links cannot be deleted without deleting the entire repo.

## Setting up

This method of creating a URL shortener is hacky and not meant to be reliable. It may break or be patched at anytime. Proceed at your own risk.

- Fork the repo.
- Set up GitHub pages for your forked repo.
- Click the Settings tab and scroll down to the GitHub Page section.
- Select the main branch source and click on the Save button.

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
5. Format for `GITHUB_ISSUES_LINK`: `https://api.github.com/repos/{owner}/{repo}/issues/` Remember to include the trailing `/`.
6. Push your changes to your database/forked repo.
