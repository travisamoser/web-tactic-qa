# Web Tactic QA

## Table of Contents
**[Developer self-QA](#developer-self-qa)**

**[Peer QA](#peer-qa)**
1. [Content and layout](#content-and-layout)
2. [Accessibility](#accessibility)
3. [Analytics](#analytics)
4. [Redirects](#redirects)
5. [Orphans](#orphans)
6. [Search](#search)
7. [Forms](#forms)
8. [Broken or redirected assets and links](#broken-or-redirected-assets-and-links)
9. [Code](#code)

    9.1. [HTML](#html)

    9.2. [JavaScript](#javascript)

    9.3. [Sass/CSS](#sasscss)
10. [Misc](#misc)
11. [Browsers](#browsers)


# Developer self-QA
After development is complete, validate content and layout. Validate every updated page of the site against the:
- Content manuscript
- SEO/Metadata document (if not in the manuscript)
- Wireframes
- Desktop PSD
- Mobile PSD

Once self-QA of each page is complete, assign the issue to the site's peer QA resource.

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

Once self-QA of this page is complete, assign the issue to the site's peer QA resource.
```

# Peer QA

## Content and layout
After Developer Self-QA is complete, validate content and layout. Validate every updated page of the site against the:
- Content manuscript
- SEO/Metadata document (if not in the manuscript)
- Wireframes
- Desktop PSD
- Mobile PSD

This validation occurs after the developer has first QA'd the page themselves and then assigned the GitHub issue to the peer QA resource.

## Accessibility
Use [pa11y](https://www.npmjs.com/package/pa11y) for accessibility testing.

This command will output all critical errors for the page, while ignoring warnings and notices and ignoring an element with the ID `myIframe`. Run the command for each page that needs tested.
```
pa11y http://www.google.com --ignore "warning;notice" --hide-elements "#myIframe"
```

Use [pa11y-ci](https://www.npmjs.com/package/pa11y-ci) to run accessibility tests against multiple URLs at once. After install, create a `.pa11yci` file.

```json
{
  "defaults": {
    "hideElements": "#myIframe",
    "ignore": [ "notice", "warning" ]
  },
  "urls": [
    "http://www.google.com/page1.html",
    "http://www.google.com/page2.html",
    "http://www.google.com/page3.html"
  ]
}
```

Then simply run:

```
pa11y-ci
```

Create a GitHub issue for accessibility testing. Here is a template:

```
TITLE:
QA: Accessibility

DESCRIPTION:
Check accessibility of each page:
- [ ] Site has no critical accessibility errors

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Analytics
Validate that the following items are added:
- Google Tag Manager container
- Google webmaster tools verification
- msvalidate verification tag
- robots.txt file in the site root
- link to sitemap.xml file in robots.txt file
- valid disallow rules in the robots.txt file
- sitemap.xml file in the site root
- valid URLs in the sitemap.xml file
- correct values for webtrends (DCSiD, fpcdom, and onsitedom parameters)

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Analytics

DESCRIPTION:
Verify analytics configuration:
- [ ] Google Tag Manager container
- [ ] Google webmaster tools verification
- [ ] msvalidate verification tag
- [ ] robots.txt file in the site root
- [ ] link to sitemap.xml file in robots.txt file
- [ ] valid disallow rules in the robots.txt file
- [ ] sitemap.xml file in the site root
- [ ] valid URLs in the sitemap.xml file
- [ ] correct values for webtrends (DCSiD, fpcdom, and onsitedom parameters)

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Redirects
Verify that:
- When the root URL is entered, redirection (if any) is correct. Ensure that a `403 Error` page is not returned.
- Redirects have been configured from deleted or renamed pages to new
- An error page has been configured to capture 404 errors
- The 404 page contains a link to obtain labeling information

Create a GitHub issue for these tasks. Here is a template:

```
TITLE:
QA: Redirects

DESCRIPTION:
Verify redirect configuration:
- [ ] When the root URL is entered, redirection (if any) is correct. Ensure that a `403 Error` page is not returned.
- [ ] Redirects have been configured from deleted or renamed pages to new
- [ ] An error page has been configured to capture 404 errors
- [ ] The 404 page contains a link to obtain labeling information

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Orphans
If an orphan check is not included in the site's build process, use `wget` to check for orphans. The following command will scrape the entire site and download all files necessary for the site. Compare the scraped site to your development folder to identify potential orphans:

```
wget -r -E -k -p -D http://www.google.com/ http://www.google.com/
```

If the site is behind authentication, use this command:

```
wget -r -E -k -p -D http://www.google.com/ http://www.google.com/ --user=XXXX.XXXX --password=XXXXXX --auth-no-challenge
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

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
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
Check forms:
- [ ] Form fields have the correct applicable validation rules applied: (e.g. Min/Max, Required, Max Length, Min Length, Input Type)
- [ ] All radio buttons and check boxes are working as intended
- [ ] Private data is transferred securely
- [ ] Integration (e.g. end to end) is working correctly and all fields are transmitted and stored sucessfullly
- [ ] Conditional logic works as intended (e.g form branching where questions are displayed based on user input)
- [ ] File upload capabilities only allows approved file types to be uploaded
- [ ] Reset button works as intended
- [ ] If user input is echoed, it is sanitized (e.g this prevents threats and vulnerabilities). (XSS Attack)

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Broken or redirected assets and links
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
- [ ] {Description of broken or redirected asset or link}
```

## Code

### HTML
#### HTMLHint errors and warnings
Check the site build for HTMLHint errors and warnings. If the site's build process does not use HTMLHint check for errors with your code editor (an extension may be required) or use the [HTMLhint NPM package](https://www.npmjs.com/package/htmlhint).

```
htmlhint "/{your-path}/**/*.{htm,html}"
```

#### W3C Markup Validation Service
Use the W3C validation service. The Validation service can be used with a browser extension:
- [Validity](https://chrome.google.com/webstore/detail/validity/bbicmjjbohdfglopkidebfccilipgeif?hl=en-GB) for Chrome
- [HTML Validator](http://users.skynet.be/mgueury/mozilla/download_090.html) for Firefox

The validation service can also be used through a [package or application](https://validator.w3.org/source/):
- [Validator S.A.C](https://habilis.net/validator-sac/) for Mac OS

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed.
- <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/html/01_overview.md>

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
Check the site build for JSHint or ESLint errors and warnings. If the site's build process does not use JSHint or ESLint check for errors with your code editor (an extension may be required).

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed.
- <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/js/01_overview.md>

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
Check the site build for SassLint or CSSLint errors and warnings. If the site's build process does not use SassLint or CSSLint check for errors with your code editor (an extension may be required).

#### Web Tactic Guardrails
Check that Web Tactic Guardrails are generally followed.
- <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/sass/01_overview.md>
- <https://github.com/tmoserfusion/web-tactic-guardrails/blob/master/css/01_overview.md>

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

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```

## Browsers
Listed below are all currently supported browser/OS combinations. At the start of the project, the developer should confirm this list in hopes of eliminating some.

Because it is used for taking screenshots, `Chrome on Mac with devtools simulting iPhone 6` is the first priority.
- Chrome on Mac with devtools simulating iPhone 6 - **FIRST PRIORITY**
- Edge on Windows 10
- IE11 on Windows 8
- IE10 on Windows 7
- Chrome (latest) on Windows 7
- Firefox (latest) on Windows 7
- Safari 10 on Mac OS 10.12
- Safari on iOS 10.3
- Chrome (latest) on Android 7.0
- Chrome (latest) on Android 6.0
- Chrome (latest) on Android 5.1
- Android Webview on Android 4.4

Create a GitHub issue for each browser. While testing, report any bugs as comments in the issue with screenshots. Here is a template:

```
TITLE:
QA: {browser} on {OS}

DESCRIPTION:
While testing, report any bugs as comments in the issue with screenshots.

## Mobile device orientation
- Test all devices in portrait orientation

## Tablet device orientation
- Test all devices in both portrait and landscape orientation

## Testing Safari on iOS
- Use the Xcode Simulator or physical devices

### Safari on iOS 10.3
- Check all three phone form-factors (iPhone SE, iPhone 7, iPhone 7+)
- Check iPad (5th generation)

## Testing Android (7.0, 6.0, 5.1, 4.4)
- Use the Virtual Device Manager found in Android Studio
- Check Galaxy Nexus (360 x 640 viewport equivalent)
- Check Galaxy Nexus 9 (728 x 1024 viewport equivalent)

For each browser check that:
- [ ] Layout matches PSDs
- [ ] Layout handles responsiveness when window is resized (desktop only)
  - [ ] Height from 768px to 1080px (including OS and browser chrome)
  - [ ] Width from 1024px to 1920px (including OS and browser chrome)
- [ ] Site navigation functions on all pages
- [ ] Sticky ISI or floating ISI functions as expected
- [ ] All interstitials function and appear as expected
- [ ] Any custom or unique UI elements (accordions, content tabs, "back to top" buttons, etc...) function and appear as expected
- [ ] Search functions as expected
- [ ] All forms function as expected
- [ ] No computer code (e.g., HTML, JavaScript etc.) displays as contextual content on any pages
- [ ] There are no Javascript errors present on any pages

COMMENTS:
- [ ] {Description of issue}
- [ ] {Description of issue}
```