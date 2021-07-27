---
title: "Hello World From Container - Flask Web App"
draft: false
showtoc: false
ShowReadingTime: false
hideSummary: false
cover: 
    image: ''
weight: 4
tags: ['Docker']
---


### Demo flask Web App to practice Docker Basics. 

### [Source Code](https://github.com/a7medayman6/Hello-World-From-Container)

### BUILD

```BASH
git clone .
cd Hello-World-From-Container
docker build -t hello-world:latest .
docker run -p 5001:5000 hello-world 
# visit http:/0.0.0.0:5001 to see the web site presnting the container id it's running from!
```

### Or pull it from docker hub!
```BASH
docker pull a7medayman6/hello-world-flask
docker run -p 5001:5000 hello-world-flask
# visit http:/0.0.0.0:5001 to see the web site presnting the container id it's running from!
```

### Preview

![2](/projects/devops/hello-world-form-container/2.png)

### Same Container name!
![1](/projects/devops/hello-world-form-container/1.png)