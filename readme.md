# Web Tactic QA

## I. Developer Self-QA
Validate content and design. Validate every updated page of the site against the:
- Content manuscript
- SEO/Metadata document (if not in the manuscript)
- Wireframes
- Desktop PSD
- Mobile PSD

Create a GitHub issue for each page with a description containing a task for each item. Here is a template:

```
TITLE:
QA: {pagename} content and layout

DESCRIPTION:
Validate page against:
- [ ] Content manuscript
      - [ ] Footer MMN number is updated
- [ ] Wireframes
- [ ] Desktop PSD
- [ ] Mobile PSD
- [ ] SEO/Metadata document (if not in the manuscript)
      - [ ] `alt` attributes for all images
      - [ ] `<title>` tag content
      - [ ] meta description tag content
      - [ ] OG tags content (if required)
```

Once the developer has completed self-QA of each page, they assign the issue to the site's peer QA resource.

## II. Peer QA

### A. Content and Layout
The peer QA resource validates every updated page of the site against the:
- Content manuscript
- SEO/Metadata document (if not in the manuscript)
- Wireframes
- Desktop PSD
- Mobile PSD

This validation occurs after the developer has first QA'd the page themselves and then assigned the GitHub issue to the peer QA resource.

### B. Code

#### 1. HTML
##### a. HTMLHint errors and warnings
Check the site build for HTMLHint errors and warnings. If the site does not have a build process that utilizes HTMLHint then use an extension or plugin in your code editor.

##### b. W3C Markup Validation Service
Copy/paste the generated HTML code to validate with the [W3C Markup Validation Service](https://validator.w3.org/#validate_by_input)

#### c. Web Tactic Guardrails
Web Tactic Guardrails are generally followed. <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/html/01_overview.md>

Create a GitHub issue for the HTML code review. In the description create tasks for each correction the developer needs to make.

```
TITLE:
QA: HTML Code Review

DESCRIPTION:
{page name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{page name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

#### 2. JavaScript

#### a. JSHint or ESLint errors and warnings
Check the site build for JSHint or ESLint errors and warnings. If the site does not have a build process that utilizes JSHint or ESLint then use an extension or plugin in your code editor.

#### b. Web Tactic Guardrails
Web Tactic Guardrails are generally followed. <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/js/01_overview.md>


Create a GitHub issue for the JavaScript code review. In the description create tasks for each correction the developer needs to make.

```
TITLE:
QA: JavaScript Code Review

DESCRIPTION:
{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

#### 3. Sass/CSS

#### a. SassLint or CSSLint errors and warnings
Check the site build for SassLint or CSSLint errors and warnings. If the site does not have a build process that utilizes SassLint or CSSLint then use an extension or plugin in your code editor.

#### b. Web Tactic Guardrails
Web Tactic Guardrails are generally followed.

<https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/sass/01_overview.md>

<https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/css/01_overview.md>

Create a GitHub issue for the Sass/CSS code review. In the description create tasks for each correction the developer needs to make.

```
TITLE:
QA: Sass/CSS Code Review

DESCRIPTION:
{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

### C. Browsers
The list of supported browsers will vary based on the project, so confirm the list. Here is a general guide.

Because it is used for taking screenshots, `Chrome on Mac with devtools simulting iPhone 6` is the first priority.
- Chrome on Mac with devtools simulating iPhone 6 (FIRST PRIORITY)
- Edge on Windows 10
- IE11 on Windows 7 or 8
- Chrome (latest) on Windows 7 or 8
- Firefox (latest) on Windows 7 or 8
- Safari 10 on Mac OS 10.12
- Safari on iOS 10
- Safari on iOS 9
- Firefox (latest) on mobile
- Chrome (latest) on mobile

Create a GitHub issue for each browser. While testing, report any bugs as comments in the issue with screenshots. Here is a template:

```
TITLE:
QA: {browser} on {OS}

DESCRIPTION:
While testing, report any bugs as comments in the issue with screenshots.

### Safari on iOS 10
- Check all three phone form-factors (iPhone SE, iPhone 7, iPhone 7+), iPad (5th gen.), and iPad Pro. Using the Xcode simulator is fine.

### Safari on iOS 9
- iOS 9 usage is probably due to older iPads. I'd recommend using the Xcode simulator to test iPad 2 running iOS 9.3.

### Firefox (latest) on mobile
- Comment in the issue with the OS you tested on.

### Chrome (latest) on mobile
- Comment in the issue with the OS you tested on.
```

### D. Analytics
Validate the following items are added:
- Google Tag Manager container
- Google webmaster tools verification
- msvalidate verification tag
- robots.txt file

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Analytics

DESCRIPTION:
- [ ] Google Tag Manager container
- [ ] Google webmaster tools verification
- [ ] msvalidate verification tag
- [ ] robots.txt file
```

### E. Redirects
Verify that:
- Redirects have been configured from old or renamed pages to new
- An error page has been configured to capture 404 errors

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Redirects

DESCRIPTION:
- [ ] Redirects have been configured from old or renamed pages to new
- [ ] An error page has been configured to capture 404 errors
```

### F. Broken or Redirected Assets and Links
Use `wget` to check for broken links. Look for any links or assets that return status codes `404`, `302`, and `301`. The following command will spider through the entire site and generate a log file in your home folder:

```
wget --spider -o ~/wget.log -e robots=off -w 1 -r -p http://www.google.com
```

If the site is behind authentication, use this command:

```
wget --spider -o ~/wget.log -e robots=off -w 1 -r -p http://www.google.com/ --user=XXXX.XXXX --password=XXXXXX --auth-no-challenge
```

Create a GitHub issue for remediation of any `404`, `302`, and `301` status codes. Here is a template:

```
TITLE:
QA: Broken or redirected assets and links

DESCRIPTION:
- [ ] {Description of broken or redirected asset or link}
```

### G. Misc
- Favicon
- All filenames (code, images, PDFs, etc…) are all lowercase

### H. Orphans
Use `wget` to check for orphans. The following command will scrape the entire site and download all files necessary for the site. Compare the scraped site to your development folder to identify potential orphans:

```
wget -r -E -k -p -D folderName http://www.google.com/
```

Create a GitHub issue for removal of any orphans. Here is a template:

```
TITLE:
QA: Orphans

DESCRIPTION:
- [ ] {Description of orphan}
```

### I. Webtech Check
- Need to get a task list for this

### J. Vulnerability Scan
- Need to get a task list for this
