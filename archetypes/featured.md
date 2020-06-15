---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
description: "{{ replace .Name "-" " " | title }}"
type: "featured"
image: "images/{{ .Name | lower }}.jpg"
bg_image: "images/{{ .Name | lower }}.jpg"
tags:
- "{{ .Name | lower }}"
---



