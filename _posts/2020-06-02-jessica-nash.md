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

## Getting Started

1. Fork the repository

1. Create your branch

1. Add your picture

Add a picture of yourself to `assets/images/avatars/`. This is the picture that will show up in the left sidebar for your poster. This picture is pretty small, so please be careful to resize your image appropriately. Please save your image as `firstName_lastName.jpg` (or whatever file extension you are using)

1. Add your information to `authors.yml`

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

If you do not have one of these or don't want to include one of the options, remove that entry starting with "label". 

4. Add a post for your poster

5. Submit a pull request

## Poster Headings and Sections

## Including Extras

### Images


### Code

#### GitHub Gist
embed code from a GitHub Gist:
<script src="https://gist.github.com/janash/7607581a759172ac45efd12c8ca38687.js"></script>

### Equations

## References
1. 
2. 

### Acknowledgements

Please include this acknowledgement for MolSSI Funding. Fill in your own name where it says `Software Fellow Name`.

"`Software Fellow Name` was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"