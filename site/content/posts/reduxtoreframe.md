+++
title = "Coming to Re-Frame from Redux"
description = "See how closely your experience with Redux will map with using Re-Frame"
tags = [
    "clojure",
    "clojurescript",
    "re-frame",
]
date = "2018-09-04"
categories = [
    "Development",
    "clojure",
]
menu = "main"
+++

Welcome! As someone who primarily writes Javascript for my day job, in either Node or React/Redux, I thought I could help bridge that gap when coming over to ClojureScript/Re-Frame land, since it is quite nice here.

I highly recommend that before anything, you read the tremendous documentation that has been provided for Re-Frame.

[Re-Frame Docs](https://github.com/Day8/re-frame/blob/master/README.md)

When you start reading through the workflow, you will immediately feel the similarities between Re-Frame and Redux. One way data flow, immutability, events/actions, event handlers/action creators. The way that it is broken down in the docs to the 6 domino system is brilliant, and I think it maps perfectly to Redux.

### Domino 1 - Event Dispatch

> React/Redux - Event

This domino is exactly the same. Withtout this, nothing happens in our application. These are the same in both applications, whether they be mouse clicks, websocket events, inputs, whatever they may be, without some event, ain't nothing happening in either application.

### Domino 2 - Event Handling

> React/Redux - Action Creator

So the events have been fired off, now what? Simliar to as in Redux, you have to dispatch this off and create what we call `actions`. And action in Redux typically contains a `type` and a `payload`. The `type` will contain a description of the change to take place, while the `payload` will contain what will be changed.

In re-frame, you are sending off a simliar `action` if you will. You dispatch a vector that will contain the type of the event as well as the payload that will be required. For example

```
[:update-name "Josh"]
```

Which will tell re-frame, dispatch and event named `update-name` with string `Josh`.

### Domino 3 - Effect Handling

> React/Redux - Reducers

So now that these have been dispatched into the Redux/Re-Frame world, now what? These are merely descriptions, now we need actual changes to be made, or what is the point? In re-frame, you write effect handlers which will be on the lookout for names of the events that we named as the `type` of action/effect in the previous domino.

In Redux, you will write reducers, which perform in a very similar manner. They receive all actions and will switch on the actions types and when there is one that they are looking for, they will grab that payload and perform some update of the app state.

In both cases, this is the domino where the changes are propagated and our app state is updated.

### Domino 4 - Query

> React/Redux - Mapping State to Props

So our app state has been updated, what next? The architecture of re-frame and Redux are the same in that the view is a function of the state. Once the state is changed, the view will then change.

In React/Redux, you will use most likely the `react-redux` library to write a function `mapStateToProps`, which will, as described map the current state of Redux to the props in your component. The way this works is that it subscribes and listens to updates in the state of redux and updates the props when this happens.

In re-frame, you again will do something vary similar and write `subscriptions` which will listen to parts of the re-frame state and update the view when the data it is subscribed to is updated.

### Domino 5 - View

> React/Redux - JSX

This is again, very simliar. You might even see a pattern! In React/Redux, we write React component using JSX which React will use to create DOM elements.

In re-frame, we use Reagent to write React components, which, as you probably guessed, will create React components.

### Domino 6 - DOM

> React/Redux - DOM

VOILA!!

Luckily for us, just like it mentions in the re-frame docs, this is handled by React / Reagent. It will take the JSX or Clojurscript we wrote and render it to the virtual dom.
