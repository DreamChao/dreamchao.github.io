---
layout: page
title: Links
description: 没有链接的博客是孤独的
keywords: 友情链接
comments: false
menu: 链接
permalink: /links/
---
* TOC
{:toc}

## Research 
### Machine Learning   
- [Nicolas Papernot](https://www.papernot.fr/)  **Working on the security and privacy of machine learning** .[Here](https://www.cleverhans.io/) is his blog.     

---

### Artificial Intelligence
- [Andrew Ng](http://www.andrewng.org/) **the expert of Artificial Intelligence**.     

---   
### Security
- [Dawn Song](https://people.eecs.berkeley.edu/~dawnsong/) **Professor of UC Berkeley**   
  -- [Selected Research Projects in Deep Learning and Security](https://people.eecs.berkeley.edu/~dawnsong/deep-learning.html)  
  --[Recent and Past Projects in Computer Security](https://people.eecs.berkeley.edu/~dawnsong/recent.html) something about Machine Learning and Security
  --[Course:Advanced Topics on Secure Haedware](https://berkeley-secure-hardware.github.io/cs294-156-f18/) about the secure hardware (enclave)

---   
### Some Organizations
- [**The Future of Humanity Institute**](http://www.fhi.ox.ac.uk/): an academic institute at Oxford devoted to research into existential risks and other long-term issues,[vacancies](http://www.fhi.ox.ac.uk/vacancies/)
- [**Cambridge Centre for the Study of Existential Risk**](http://cser.org/): an academic institute at Cambridge devoted to research into and advocacy concerning existential risks
- [**Future of Life Institute**](http://futureoflife.org/): a volunteer-run research and outreach organisation working to mitigate existential risks
- [**Machine Intelligence Research Institute**](https://intelligence.org/): a non-profit research institute doing technical research into how to align AI with human values,[vacancies](https://intelligence.org/get-involved/#careers)
- [**Google Deep Mind**](http://deepmind.com/): the leading for-profit company developing AGI
- [**OpenAI**](https://openai.com/about/)
- [**Berkeley Center for Human-Compatible AI**](https://humancompatible.ai/)
- [ **Berkeley Artificial Intelligence Research (BAIR) Lab**](https://bair.berkeley.edu/)   


---  
## Others

> God made relatives. Thank God we can choose our friends.

{% for link in site.data.links %}
  {% if link.src == 'life' %}
* [{{ link.name }}]({{ link.url }})
  {% endif %}
{% endfor %}

> 友情链接

{% for link in site.data.links %}
  {% if link.src == 'www' %}
* [{{ link.name }}]({{ link.url }})
  {% endif %}
{% endfor %}   
