---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: ""
type: "post"
image: "images/{{ .Name | lower }}.jpg"
bg_image: "images/{{ .Name | lower }}.jpg"
categories:
- "{{ .Name | lower }}"
tags:
- "{{ .Name | lower }}"
---



