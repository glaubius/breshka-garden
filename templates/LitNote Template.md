---
title: 
draft: false
tags:
  - "#litnote"
---

## @{{citekey}}
Title: {{title}}
Year: {{date | format ("YYYY")}}
Authors: {{authors}}

### Annotations
{% persist "annotations" %}
{% set newAnnotations = annotations | filterby("date", "dateafter", lastImportDate) %}
{% if newAnnotations.length > 0 %}

#### Imported: {{importDate | format("YYYY-MM-DD h:mm a")}}

{% for a in newAnnotations %}
{% if a.annotatedText.length > 0 %}
> {{a.annotatedText}} (p. {{a.page}})
{% endif %}
{% if a.ocrText %}
>{{a.octText}}
{% endif %}
{% if a.comment %}
>**comment:**
>{{a.comment}}
{% endif %}
{% endfor %}

{% endif %}
{% endpersist %}