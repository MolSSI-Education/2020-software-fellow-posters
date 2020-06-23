---
name: sample-poster
title: Establishing a general framework to represent molecular wavefunctions and provide simple interoperability
author: "Sebastian Lee"
mentor-names: "Taylor Barnes"
full-author-list:
    - name: "Sebastian J. R. Lee"
      affiliation: 1
    - name: "Thomas F. Miller III"
      affiliation: 1
affiliations:
    - name: "Department of Chemistry and Chemical Engineering, California Institute of Technology"
      address: "Pasadena, CA"
      index: 1
toc: true
toc_sticky: true
toc_label: "Poster Contents"
layout: poster
---

## Introduction

images:

![NSF Logo]({{ site.url }}{{ site.baseurl }}/assets/images/sample-poster/nsf.png)  
***Figure 1**: The logo of the National Science Foundation.*


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

#### Backticks

If you don't want line numbers you can use three backticks to start a code block, and three backticks to end the code block. The language should follow the first three backticks.

````markdown

```LANGUAGE

  YOUR CODE HERE

 ``` 

````

## References
1. 
2. 

### Acknowledgements

"Sebastian Lee was supported by a fellowship from The Molecular Sciences Software Institute under NSF grant OAC-1547580"
