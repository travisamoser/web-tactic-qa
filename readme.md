# Web Tactic QA
---

# Developer Self-QA
Validate content and layout. Validate every updated page of the site against the:
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
      - [ ] The page has links to the label components (PI, PPI, UG, MG)
  - [ ] `<h1>` tag (at least one per page)
- [ ] SEO/Metadata document (if not in the manuscript)
      - [ ] `alt` attributes for all images
      - [ ] `<title>` tag content
      - [ ] meta description tag content
      - [ ] OG tags content (if required)
- [ ] Wireframes
- [ ] Desktop PSD
- [ ] Mobile PSD
```

Once the developer has completed self-QA of each page, they assign the issue to the site's peer QA resource.

# Peer QA

## Content and Layout
The peer QA resource validates every updated page of the site against the:
- Content manuscript
- SEO/Metadata document (if not in the manuscript)
- Wireframes
- Desktop PSD
- Mobile PSD

This validation occurs after the developer has first QA'd the page themselves and then assigned the GitHub issue to the peer QA resource.

## Code

### HTML
#### HTMLHint errors and warnings
Check the site build for HTMLHint errors and warnings. If the site's build process does not use HTMLHint check for errors with an extension to your code editor.

#### W3C Markup Validation Service
Use the W3C validation service. The Validation service can be used with a browser extension:
- [Validity](https://chrome.google.com/webstore/detail/validity/bbicmjjbohdfglopkidebfccilipgeif?hl=en-GB) for Chrome
- [HTML Validator](http://users.skynet.be/mgueury/mozilla/download_090.html) for Firefox

The validation service can also be used through a [package or application](https://validator.w3.org/source/):
- [Validator S.A.C](https://habilis.net/validator-sac/) for Mac OS

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed. <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/html/01_overview.md>

Create a GitHub issue for the HTML code review. In the comments create tasks for each correction the developer needs to make.

```
TITLE:
QA: HTML Code Review

DESCRIPTION:
Perform HTML code review
- [ ] No HTMLHint errors or warnings found
- [ ] Markup validates per W3C spec
- [ ] Code generally follows web tactic guardrails

COMMENT:
{page name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{page name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

### JavaScript

#### JSHint or ESLint errors and warnings
Check the site build for JSHint or ESLint errors and warnings. If the site's build process does not use JSHint or ESLint check for errors with an extension to your code editor.

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed. <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/js/01_overview.md>

Create a GitHub issue for the JavaScript code review. In the comments create tasks for each correction the developer needs to make.

```
TITLE:
QA: JavaScript Code Review

DESCRIPTION:
Perform JavaScript code review
- [ ] No JSHint/ESLint errors or warnings found
- [ ] Code generally follows web tactic guardrails

COMMENT:
{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

### Sass/CSS

#### SassLint or CSSLint errors and warnings
Check the site build for SassLint or CSSLint errors and warnings. If the site's build process does not use SassLint or CSSLint check for errors with an extension to your code editor.

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed.

<https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/sass/01_overview.md>

<https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/css/01_overview.md>

Create a GitHub issue for the Sass/CSS code review. In the comments create tasks for each correction the developer needs to make.

```
TITLE:
QA: Sass/CSS Code Review

DESCRIPTION:
Perform Sass/CSS code review
- [ ] No SassLint/CSSLint errors or warnings found
- [ ] Code generally follows web tactic guardrails

COMMENT:
{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}

{File name}
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Browsers
The list of supported browsers will vary based on the project, so confirm the list. Here is a general guide.

Because it is used for taking screenshots, `Chrome on Mac with devtools simulting iPhone 6` is the first priority.
- Chrome on Mac with devtools simulating iPhone 6 (FIRST PRIORITY)
- Edge on Windows 10
- IE11 on Windows 7 or 8
- Chrome (latest) on Windows 7 or 8
- Firefox (latest) on Windows 7 or 8
- Safari 10 on Mac OS 10.12
- Safari on iOS 10 (portrait)
- Safari on iOS 9 (portrait)
- Chrome (latest) on Galaxy S6 Phone Android 5.0 (portrait)
- Chrome (latest) on Nexus 9 Tablet Android 5.0 (portrait)

Create a GitHub issue for each browser. While testing, report any bugs as comments in the issue with screenshots. Here is a template:

```
TITLE:
QA: {browser} on {OS}

DESCRIPTION:
While testing, report any bugs as comments in the issue with screenshots.

### Safari on iOS 10
- Check all three phone form-factors (iPhone SE, iPhone 7, iPhone 7+) with the the Xcode Simulator.
- Check iPad (5th generation) with the the Xcode Simulator.

### Safari on iOS 9
- iOS 9 usage can probably be attributed to older iPads. Use the Xcode simulator to test iPad 2 running iOS 9.3.

### Chrome (latest) on Android 5
- For phone, check Samsung Galaxy S6 in portrait (360 x 640) at <https://crossbrowsertesting.com>
- For tablet, check HTC Nexus 9 in portrait (768 x 1024) at <https://crossbrowsertesting.com>

For each browser check that:
- [ ] Site navigation functions on all pages
- [ ] No computer code (e.g., HTML, JavaScript etc.) displays as contextual content on any pages
- [ ] There are no Javascript errors present on any pages
```

## Analytics
Validate that the following items are added:
- Google Tag Manager container
- Google webmaster tools verification
- msvalidate verification tag
- robots.txt file is in the site root
- robots.txt file includes a link to sitemap.xml file
- Disallow rules in the robots.txt are all valid
- sitemap.xml file is in the site root
- sitemap.xml file's URLs are all valid
- Check that DCSiD, fpcdom, and onsitedom parameters at configuration file has been populated with the appropriate value for your site's webtrends account

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Analytics

DESCRIPTION:
- [ ] Google Tag Manager container
- [ ] Google webmaster tools verification
- [ ] msvalidate verification tag
- [ ] robots.txt file is in the site root
- [ ] robots.txt file includes a link to sitemap.xml file
- [ ] Disallow rules in the robots.txt are all valid
- [ ] sitemap.xml file is in the site root and URLs are all valid
- [ ] sitemap.xml file's URLs are all valid
- [ ] Check that DCSiD, fpcdom, and onsitedom parameters at configuration file has been populated with the appropriate value for your site's webtrends account
```

## Redirects
Verify that:
- When the root URL is entered, redirection (if any) is correct. Ensure that there is no `403 Error` page returned.
- Redirects have been configured from old or renamed pages to new
- An error page has been configured to capture 404 errors
- The 404 page contains a link to obtain labeling information

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Redirects

DESCRIPTION:
- [ ] When the root URL is entered, redirection (if any) is correct. Ensure that there is no `403 Error` page returned.
- [ ] Redirects have been configured from old or renamed pages to new
- [ ] An error page has been configured to capture 404 errors
- [ ] The 404 page contains a link to obtain labeling information
```

## Broken or Redirected Assets and Links
Use `wget` to check for broken links. Look for any links or assets that return status codes `404`, `302`, and `301`. The following command will spider through the entire site and generate a log file in your home folder:

```
wget --spider -o ~/wget.log -e robots=off -w 1 -r -p http://www.google.com
```

If the site is behind authentication, use this command:

```
wget --spider -o ~/wget.log -e robots=off -w 1 -r -p http://www.google.com/ --user=XXXX.XXXX --password=XXXXXX --auth-no-challenge
```

Create a GitHub issue for checking for broken or redirected assets and links. Include comments for remediation of any `404`, `302`, and `301` status codes. Here is a template:

```
TITLE:
QA: Broken or redirected assets and links

DESCRIPTION:
- [ ] Use wget to check for broken or redirected assets and links

COMMENTS:
- [ ] {Description of broken or redirected asset or link}
```

## Misc
- Favicon created and linked correctly
- All filenames (code, images, PDFs, etc…) are all lowercase. Run this terminal command in your `dist` directory (or equivalent) to output a list of files containing uppercase letters:

  `find . -ls | grep '.*/[A-Z]' > output.txt`


Create a GitHub issue for miscellaneous bugs. Here is a template:

```
TITLE:
QA: Misc

DESCRIPTION:
- [ ] Favicon created and linked correctly
- [ ] All filenames (code, images, PDFs, etc…) are all lowercase
```

## Orphans
If an orphan check is not included in the site's build process, use `wget` to check for orphans. The following command will scrape the entire site and download all files necessary for the site. Compare the scraped site to your development folder to identify potential orphans:

```
wget -r -E -k -p -D folderName http://www.google.com/
```

Create a GitHub issue for an orphan check. Here is a template:

```
TITLE:
QA: Orphans

DESCRIPTION:
- [ ] Site checked for orphans

COMMENTS:
- [ ] {Description of orphan}
- [ ] {Description of orphan}
```

## Search
Check that site search functionality only includes content within the website domain (specifically, not allowing cross site search). A search term will be selected from another Lilly web site not related to this one. The search results will be examined for any results that do not pertain to the web site being checked.

Create a GitHub issue for search functionality. Here is a template:

```
TITLE:
QA: Search

DESCRIPTION:
- [ ] Site search functionality only includes content within the website domain (specifically, not allowing cross site search). A search term will be selected from another Lilly web site not related to this one. The search results will be examined for any results that do not pertain to the web site being checked.
```

## Forms
- Form fields have the correct applicable validation rules applied: (e.g. Min/Max, Required, Max Length, Min Length, Input Type)
- All radio buttons and check boxes are working as intended
- Private data is transferred securely
- Integration (e.g. end to end) is working correctly and all fields are transmitted and stored sucessfullly
- Conditional logic works as intended (e.g form branching where questions are displayed based on user input)
- File upload capabilities only allows approved file types to be uploaded
- Reset button works as intended
- If user input is echoed, it is sanitized (e.g this prevents threats and vulnerabilities). (XSS Attack)

Create a GitHub issue for form bugs. Here is a template:

```
TITLE:
QA: Forms

DESCRIPTION:
- [ ] Form fields have the correct applicable validation rules applied: (e.g. Min/Max, Required, Max Length, Min Length, Input Type)
- [ ] All radio buttons and check boxes are working as intended
- [ ] Private data is transferred securely
- [ ] Integration (e.g. end to end) is working correctly and all fields are transmitted and stored sucessfullly
- [ ] Conditional logic works as intended (e.g form branching where questions are displayed based on user input)
- [ ] File upload capabilities only allows approved file types to be uploaded
- [ ] Reset button works as intended
- [ ] If user input is echoed, it is sanitized (e.g this prevents threats and vulnerabilities). (XSS Attack)
```
