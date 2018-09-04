+++
title = "Getting Started with Hugo"
description = "Goto hugo releases and download the appropriate version for your os and architecture."
tags = [
    "clojure",
    "clojurescript",
    "re-frame",
]
date = "2018-09-03"
categories = [
    "Development",
    "clojure",
]
menu = "main"
+++

Welcome! As someone who primarily writes Javascript in either Node or React/Redux, I thought I could help bridge that gap when coming over to ClojureScript/Re-Frame land, becuase it is quite nice here.

I highly recommend that before anything, you read the tremendous documentation that has been provided for Re-Frame.

[Re-Frame Docs](https://github.com/Day8/re-frame/blob/master/README.md)

When you start reading through the workflow, you will immediately feel the similarities between Re-Frame and Redux. One way data flow, immutability, events/actions, event handlers/action creators. The way that it is broken down in the docs to the 6 domino system is brilliant, and I think it maps perfectly to Redux.

### Domino 1

Re-Frame - Event Dispatch
React/Redux - Event

This domino is exactly the same. Withtout this, nothing happens in our application. These are the same in both applications, whether they be mouse clicks, websocket events, inputs, whatever they may be, without some event, ain't nothing happening in either application.

### Domino 2

Re-Fream - Event Handling
React/Redux - Action Creator
