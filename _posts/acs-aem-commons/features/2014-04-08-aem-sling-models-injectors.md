---
layout: acs-aem-commons_feature
title: AEM Objects Sling Models Injector
description: Inject AEM objects into your Sling Models classes
date: 2014-04-08 23:39:29
thumbnail: /images/aem-sling-models-injectors/thumbnail.png
categories: acs-aem-commons features
feature-tags: backend-dev
tags: acs-aem-commons-features
initial-release: 1.6.0
---

## Purpose

Allows for [Sling Models](http://sling.apache.org/documentation/bundles/models.html) classes and interfaces to be injected with common AEM-related objects, namely those made available using `<cq:defineObjects/>`:

* `resource`
* `resourceResolver`
* `componentContext`
* `pageManager`
* `currentPage`
* `resourcePage`
* `designer`
* `currentDesign`
* `resourceDesign`
* `currentStyle`
* `session`
* `xssApi`

Most injections are available when adapting either a `Resource` or `SlingHttpServletRequest` object, with these exceptions, which only work when adapting a `SlingHttpServletRequest` object:

* `currentPage`
* `componentContext`
* `xssApi`
* `currentDesign`

## Example

    @Model(adaptables = { SlingHttpServletRequest.class, Resource.class })
    public class TestModel {

        @Inject
        private Page resourcePage;

        public Page getResourcePage() {
            return resourcePage;
        }
    }