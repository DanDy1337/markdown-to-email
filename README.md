[![Gitpod ready-to-code](https://img.shields.io/badge/Gitpod-ready--to--code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/atherdon/markdown-to-email)


install  "pixel-email-cli" and try it https://github.com/LLazyEmail/pixel-email-cli

Maintainer notes:

- Replacer v.0.4 working fine
- Methods in package/* might be broken for some time
- **Generator Module was moved out into https://github.com/LLazyEmail/generator-module**
- **Replacer for React DOM right now is broken. I'm moving it out into https://github.com/LLazyEmail/react-plain-template-example**
- **React version isn't working now. Probably we'll skip few releases and make it work as it should be.**

# Markdown to email template generator

This simple and light tool generates email template from markdown. The command is `npm run parse`. 
The path to markdown file must be `./source/source.md`, and output directory is `generated/newEmail.html`.

We tried to create our own wheel, then we failed. Arthur get bored trying to fix it and make it work properly.
So he just decide to google a working version that can solve his problems.

Story: 
0. I find this link https://gist.github.com/jbroadway/2836900
1. then this link https://gist.github.com/budparr/112f08a3033dd878d0e271e2af61faef
2. and then I added javascript into my google Search https://gist.github.com/renehamburger/12f14a9bd9297394e5bd
3. then we tried different approaches, failed few times and find out how to fix some bugs.
4. then I tried to google our repository and find out the latest version of this module - https://github.com/showdownjs/showdown
5. then I find out that all template engines still sucks and decide to migrate "frontend" part to react
6. i'm exploring the best known to me tools for markdown: remark and rehype. plus, as docusaurus using them and mdx format - we'll try it too

how to run a parser

```yarn parse```

if you need help with markdown - Great Online Preview tool https://dillinger.io/


## Syntax
Parser uses no libraries, so it copies markdown syntax and based on opening tag generates email component (image, paragraph, subtitle, etc.). There is a list of existing tags:

### Subject
```
#!
```
The subject of email, will be displayed in the email preview.

### Preview text
```
#~
```
Preview text of email, will be displayed in the email preview.

### Title
```
#
```
Title of email, by default at the top of email body.

### Subtitle
```
##
```
Subtitle, can be seen anywhere in email body.

### Sponsorship
```
~[content][href][src]
```
The first symbol should be tilde `~`, and all other attributes should be not empty, or this will cause errors. `src` - absolute path to image or may be url, `href` - the link of sponsorship block, `content` - the text near the image (also link, wrapped in `href`). Where ever you place sponsorship block, it will be concatenated and parsed at the top and bottom of email body.

### Image or GIF
```
![src][href][alt text]
```
The first symbol `!`, and all other attributes are required, or error will appear. `src` - absolute path to image or may be url, `href` - the link of image, `alt text` - the text, when image not rendered yet.

### Paragraph
Default paragraph contains no special opening symbols, just straight text.

### Link
```
[content](href)
```
Consist of two parameters - `content`, the text of the link and `href` - the url of link. Can be placed at default paragraph.

### Divider
You may use empty line in email body, just in the markdown document leave line empty, it will be parsed as real line break.

### Separator
add `[separator]`

## Work principles
The parser reads source file from `source/source.md` and based on opening tag renders goes in `layouts` folder and chooses relevant typography or section (sponsorship) element. Supported tags displayed in this document.

![mindmap](https://github.com/atherdon/markdown-to-email/blob/main/MindMap1.png?raw=true)

## Reasons to use generator instead of pretending that human errors didnt exists(especially human reactions on deadlines)

![oops](https://raw.githubusercontent.com/atherdon/markdown-to-email/main/Correction.png)

![ooops2](https://raw.githubusercontent.com/atherdon/markdown-to-email/main/Oops-I.png)

Links
- https://codepen.io/rh/pen/BoyNdy
- https://gist.github.com/renehamburger/12f14a9bd9297394e5bd
- https://github.com/Chalarangelo/parse-md-js/blob/master/parsemd.js
- https://www.bigomega.dev/markdown-parser
- https://gist.github.com/budparr/112f08a3033dd878d0e271e2af61faef
- https://gist.github.com/jbroadway/2836900
- https://stackoverflow.com/questions/47016770/replace-markdown-characters-with-regex


- https://www.htmlemailcheck.com/check/


## Stretch Goals (enchancements)

- add html linter
because it's hard to understand if everything is good or not

https://www.npmjs.com/package/eslint-plugin-html

we can use https://www.freeformatter.com/html-validator.html and see errors. not sure if they actually valid, but will be cool to pay attention to some of them

![image](https://user-images.githubusercontent.com/1469198/96992186-2fd57b00-1532-11eb-8709-f18dde099c7c.png)

- add links checker

![image](https://user-images.githubusercontent.com/1469198/101926544-f937ea80-3bdb-11eb-8df8-0ca4250c54b0.png)


good example is December/top1 newsletter

- https://www.npmjs.com/package/broken-link-checker
- https://www.npmjs.com/package/link-checker
- https://www.npmjs.com/package/link-check



Check later:
- https://maizzle.com/
- https://www.npmjs.com/package/verymail
- https://www.npmjs.com/package/markdown-to-mailchimp

- https://www.npmjs.com/package/simple-markdown

"amazing tool that can solve a lot of issues": https://github.com/syntax-tree/mdast


----

https://www.npmjs.com/package//sanitize-html

https://www.npmjs.com/package/html-element-attributes

https://www.npmjs.com/package/html-tag

https://github.com/breakdance/breakdance

https://github.com/here-be/snapdragon

https://github.com/wooorm/html-element-attributes

https://www.npmjs.com/package/element-mold

---

https://www.npmjs.com/package/yargs

https://www.npmjs.com/package/commander

---

- https://tomassetti.me/parsing-in-javascript/
- https://github.com/aaditmshah/lexer
- https://github.com/zaach/jison


----


- https://github.com/MarcL/markdown-to-mailchimp

- https://github.com/pluralsight/htmlTagValidator


----
Cool projects to see

- https://github.com/Slicejack/bojler
- https://github.com/maizzle/maizzle
- https://github.com/sglazov/pechkin
- https://github.com/5t3ph/11ty-email-generator/blob/main/src/_data/meta.js
- 
