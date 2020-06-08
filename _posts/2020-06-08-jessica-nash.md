---
name: sample-poster
title: How to add your Poster
author: "Jessica Nash"
full-author-list:
    - name: "Jessica A. Nash"
      affiliation: 1
    - name: "Second Author"
      affiliation: 2
    - name: "Third Author"
      affiliation: 2
affiliations:
    - name: "The Molecular Sciences Software Institute"
      address: "Blacksburg, VA"
      index: 1
    - name: "Department of Chemistry, Virginia Tech University"
      index: 2
      address: "Blacksburg, VA"
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

## Introduction

This is a template to create an online poster for your software project.

You can include equations:

$$ \vec{F} = - \nabla U $$

$$ \vec{F} = m \cdot \vec{a} = m \cdot \frac{d\vec{v}}{dt} = m \cdot \frac{d^{2}\vec{r}}{dt^{2}}$$

images:

![NSF Logo]({{ site.url }}{{ site.baseurl }}/assets/images/sample-poster/nsf.png)  
***Figure 1**: The logo of the National Science Foundation.*

and code:

{% highlight python wl linenos %}
import numpy as np

for atom1 in atoms:
    for atom2 in atoms:
        a1 = atoms.index(atom1)
        a2 = atoms.index(atom2)
        coor1 = coordinates[a1]
        coor2 = coordinates[a2]
        distance = np.sqrt(np.sum((coor1-coor2)**2))
        if 0 < distance <= 1.5:
            print(F'{atom1:2} to {atom2:2} : {distance:.3f}')

def hello_world():
    print("hello world")

{% endhighlight %}

## Adding your poster

### Fork the repository

This website uses a Jekyll template on GitHub pages. You will add your poster by adding a markdown file and editing a yaml (directions below). You will need to Fork [the Repository](https://github.com/MolSSI-Education/2020-software-fellow-posters) and submit a pull request to have your poster added.

### Create a branch on your fork

Create a branch to work on.

```bash
$ git checkout -b YOUR_NAME
```

### Add your picture

Add a picture of yourself to `assets/images/avatars/`. This is the picture that will show up in the left sidebar for your poster. This picture is pretty small, so please be careful to resize your image appropriately. Please save your image as `firstName_lastName.jpg` (or whatever file extension you are using)

### Add your information to `authors.yml`

There is a file in this repository at `_data/authors.yml`. You should add your author information to this. You can see my example in the repo, and a template is given below: 

  ```yaml
YOUR NAME:
    name    : "YOUR NAME"
    bio     : "Your position and institution"
    avatar  : "/assets/images/avatars/firstName_lastName.jpg"
    links   :
      - label: "Email"
        icon: "fas fa-fw fa-envelope-square"
        url: "mailto:YOUREMAIL@something.con"
      - label: "Website"
        icon: "fas fa-fw fa-link"
        url: "YOUR WEBSITE"
      - label: "Twitter"
        icon: "fab fa-fw fa-twitter-square"
        url: "https://twitter.com/YOUR_TWITTER_HANDLE"
      - label: "GitHub"
        icon: "fab fa-fw fa-github"
        url: "https://github.com/YOUR_GITHUB_NAME"
      - label: "LinkedIn"
        icon: "fab fa-fw fa-linkedin"
        url: "https://www.linkedin.com/in/YOURLINKEDIN/"
```

You should edit your name and links to websites. If you do not have one of these or don't want to include one of the options, remove that entry starting with "label". 

### Add a post for your poster

To add a poster, go to the `_posts` directory in the top level of this repository. You can copy this file as a starting point. Change the file name so that the file name is `YEAR_MONTH_DAY-firstName-lastName.md`. 

### Submit a pull request

Once you have finished your poster, push to your fork and submit a pull request on the main MolSSI repo.

## Poster Headings and Sections

The Table of Contents on the right will be rendered automatically based on your poster sections. Sections should be labeled using `##` markdown tags.

## Including Extras

Here are some directions on how to include extras like images, equations, and code. Not that you should not copy and paste the examples from the markdown file (rendered page is fine), as the examples in this section have some special characters so that the code can be rendered on the site.

### Images

If you include images on your poster, please make a directory for your poster under `assets/images`. Please make the directory name your name so that the path to your images will be `assets/images/FIRSTNAME_LASTNAME/`.

For images to show up on your poster, you must use this syntax. You can use the example in the Introduction (NSF logo).

```markdown
![Figure Label]({{ "{{ site.url" }} }}{{ "{{ site.baseurl" }} }}/assets/images/FIRSTNAME_LASTNAME/your_image.png)  
***Figure 1**: The logo of the National Science Foundation.*
```

### Code

There are a few ways you might include code snippets in this template. For the first two (markdown highlight tag and using back tick characters) you will include your code on the page. For the GitHub gist, you create a gist on GitHub and embed the script.

#### Highlight tag

Surround your code with a special tag. This example will highlight a code and add line numbers.

```markdown
{{ "{% highlight LANGUAGE wl linenos " }}%}
  YOUR CODE HERE
{{ "{% endhighlight "}}%}

```

#### Backticks

If you don't want line numbers you can use three backticks to start a code block, and three backticks to end the code block. The language should follow the first three backticks.

````markdown

```LANGUAGE

  YOUR CODE HERE

 ``` 

````

#### GitHub Gist
You can embed code from a GitHub Gist. If you have a gist, you can get the code for your script on the page for the gist by copying the code from the 'Embed' button. It will look something like this:
```
<script src="https://gist.github.com/janash/7607581a759172ac45efd12c8ca38687.js"></script>
```

### Equations
Equations are supported through [MathJax](https://www.mathjax.org). MathJax allows you to use LaTex format for your equations. Here are some example equations

```
$$ \vec{F} = - \nabla U $$

$$ \vec{F} = m \cdot \vec{a} = m \cdot \frac{d\vec{v}}{dt} = m \cdot \frac{d^{2}\vec{r}}{dt^{2}}$$
```

And you can see more documentation [here](http://docs.mathjax.org/en/latest/basic/mathematics.html).

## Previewing the site locally

You can preview this site locally by installing [jekyll](https://jekyllrb.com). Once you have jekyll installed, you can preview the site by doing

```bash
$ bundle exec jekyll serve
```

in the top level of this repository. A preview of the site will be lon `localhost:4000`

## References
1. 
2. 

### Acknowledgements

Please include this acknowledgement for MolSSI Funding. Fill in your own name where it says `Software Fellow Name`.

"`Software Fellow Name` was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"