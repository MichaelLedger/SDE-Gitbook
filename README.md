# SDE-Gitbook

[Setup and Installation of GitBook](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md)

Software design engineer examination book published with Gitbook.

#### Install Homebrew
`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
#### Install node
`brew install node`
#### Lookup version
`node -v`
`npm -v`

#### upgrade node to stable version
```
% sudo n stable
Password:
  installing : node-v16.17.1
       mkdir : /usr/local/n/versions/node/16.17.1
       fetch : https://nodejs.org/dist/v16.17.1/node-v16.17.1-darwin-x64.tar.xz
     copying : node/16.17.1
   installed : v16.17.1 (with npm 8.15.0)
```

#### upgarde npm install -g npm

#### Global install gitbook
`$ sudo npm install gitbook-cli -g`

#### Install plugins
`$ cd SDE && gitbook install`

***
Preview locally in Safari with command:
```
% gitbook serve SDE
```
Publish book with command:
```
% gitbook build SDE
```
***
#### Gitbook commands
Use `$ gitbook init <dir>`  to create a book

Use `$ gitbook install <dir>`  to install plugins for book from book.json into `node_modules` directory

Use `$ gitbook build <dir>` to build a book

Use `$ gitbook serve <dir>` to preview a book
***
#### Gitbook installation issues

**Gitbook-cli install error TypeError: cb.apply is not a function inside graceful-fs**
```
TypeError: cb.apply is not a function
    at /usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:287:18
    at FSReqCallback.oncomplete (fs.js:177:5)
```

The issue was originally a problem inside graceful-fs but they solved it in this commit I believe.

The problem is that GitBook is still using outdated dependencies that pull in versions of graceful-fs without the fix.

The solution I found was to update graceful-fs inside gitbook like this:

If you've installed gitbook globally by doing npm install -g gitbook-cli then your path in macOS should be something like

`/usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules`. 

Your path may differ depending on your OS or installation location.

Run this:
```
cd /usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/
npm install graceful-fs@latest --save
```
Then try installing GitBook. It should have fixed the installing problem.

**Gitbook-cli install error TypeError: Cannot read property 'pipes' of undefined**
```
TypeError: Cannot read property 'pipes' of undefined
    at ReadStream.Readable.pipe (_stream_readable.js:643:13)
    at /Users/gavin/.gitbook/versions/3.2.3/node_modules/cpr/lib/index.js:163:22
    at callback (/usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/graceful-fs/polyfills.js:299:20)
    at FSReqCallback.oncomplete (fs.js:176:21)
```

```
System：archlinux

I can not uninstall the gitbook CLI version: 2.3.2 with

npm uninstall gitbook-cli -g ,

and then run

npm install gitbook-cli@2.1.2 --global

nothing happened.

I sloved it by

cd ~/.gitbook/versions/3.2.3/node_modules/npm/node_modules/
vim package.json 

change the version of graceful-fs to 4.2.0,and then

npm install

after that, everything is ok.

what's more, my node version is 12.22 , if node version is 14 up, that may cause other problems.
```

Personal Resolution:

```
% cd /usr/local/lib/node_modules/gitbook-cli/node_modules/npm/node_modules/
% npm install graceful-fs@latest --save
```
After installed graceful-fs@latest (graceful-fs@4.2.6), start install gitbook.

```
% npm uninstall gitbook-cli -g
% npm install gitbook-cli -g

% gitbook --version
CLI version: 2.3.2
GitBook version: 3.2.3
```
Then rollback graceful-fs@4.2.0 to make sure that gitbook install plugins success.
```
% npm install graceful-fs@4.2.0 --save 

+ graceful-fs@4.2.0
updated 1 package and audited 395 packages in 4.533s
found 78 vulnerabilities (31 low, 25 moderate, 22 high)
  run `npm audit fix` to fix them, or `npm audit` for details
```
