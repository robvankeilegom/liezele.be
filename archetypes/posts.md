---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: ""
type: "post"
image: "images/posts/{{ .Name | lower }}.jpg"
bg_image: "images/posts/{{ .Name | lower }}.jpg"
categories:
- "{{ .Name | lower }}"
tags:
- "{{ .Name | lower }}"
---



