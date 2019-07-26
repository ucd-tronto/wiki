# wiki

Overall project TODOs and other information.

## Literature review

To generate the table of contents for the [literature review page](literature.md), first ensure that [npm](https://www.npmjs.com/get-npm) is installed. Then run

```
sudo npm install --global markdown-toc
```

to install the markdown-toc CLI. Then run

```
markdown-toc --no-firsth1 literature.md
```

to get the TOC output to the terminal.
