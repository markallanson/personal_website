---
title: 'Running a Pandoc build on Vercel'
date: 15/11/2020T10:56:00.000Z
author: Mark
layout: post
categories:
  - pandoc
  - cv
---
For the last year or so I have been maintaining my CV/Resume as a series of Markdown files stored
in git. These files are then combined into a full document and output into html, pdf, docx using
pandoc. 

I was performing the build and publication of updates to the document manually, but as is typical
of a software engineer I wanted something with a bit less friction which didn't prevent me from
making changes due the amount of work involved.

Enter [Vercel] - automated serverless static website publishing triggered from git commits. The 
process is pretty simple:

   1. Tell Vercel what repository and branch to monitor (in my case, [GitHub])
   2. Tell it how to build
   3. Tell it where the output goes
   4. Setup a custom domain

Vercel has a lot of build presets, but unless you are doing something very basic you will need
to override the standard build settings. This is certainly the case with Pandoc. Vercel runs on
AWS and the build images are [Amazon Linux 2] and use yum package management but the repositories
and standard build image is very light. The suggestion to use [EPEL] is fair but it contains 
an outdated version of Pandoc.

This is how I got everything to hang together and build on Vercel. First, setup the EPEL repository
as it does contain some packages we need. Then install some dependencies. In my case I am using 
[wkhtmltopdf] to generate the PDF.


```
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install wkhtmltopdf
```

Now we need to install a recent version of Pandoc manually from their release repository, as the
version in EPEL is only 1.x at the time of writing.

```
yum install wget
mkdir pandoc
wget -qO- https://github.com/jgm/pandoc/releases/download/2.11.1.1/pandoc-2.11.1.1-linux-amd64.tar.gz | \
   tar xvzf - --strip-components 1 -C ./pandoc
export PATH="./pandoc/bin:$PATH"
```

wkhtmltopdf requires an X server, so in this case we can run it when we run wkhtmltopdf by wraping
it in a shell script that starts the virtual X server prior to wkhtmltopdf being called and create 
a symlink so the shell script is run when wkhtmltopdf is invoked.

```
printf '#!/bin/bash\nxvfb-run -a --server-args="-screen 0, 1024x768x24" /usr/bin/wkhtmltopdf -q $*' \
  > /usr/bin/wkhtmltopdf.sh
chmod a+x /usr/bin/wkhtmltopdf.sh
ln -s /usr/bin/wkhtmltopdf.sh /usr/local/bin/wkhtmltopdf
``` 

Now all the pieces are in place you can run a pandoc build to generate your document.

[Vercel]: https://vercel.com/dashboard
[GitHub]: https://github.com/
[Amazon Linux 2]: https://aws.amazon.com/amazon-linux-2/
[EPEL]: https://fedoraproject.org/wiki/EPEL
[wkhtmltopdf]: https://wkhtmltopdf.org/