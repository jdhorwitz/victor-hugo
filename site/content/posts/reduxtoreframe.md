+++
title = "Coming to Re-Frame from Redux"
description = "See how closely your experience with Redux will map with using Re-Frame"
tags = [
    "clojure",
    "clojurescript",
    "Re-Frame",
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

[Re-Frame Docs](https://github.com/Day8/Re-Frame/blob/master/README.md)

When you start reading through the workflow, you will immediately feel the similarities between Re-Frame and Redux. One way data flow, immutability, events/actions, event handlers/action creators. The way that it is broken down in the Re-Frame docs in the 6 domino system is brilliant, and I think it maps perfectly to Redux.

### Domino 1 - Event Dispatch

> React/Redux - Event

This domino is exactly the same. Without this, nothing happens in our application. These are the same in both applications, whether they be mouse clicks, websocket events, inputs, whatever they may be, without some event, ain't nothing happening in either application.

### Domino 2 - Event Handling

> React/Redux - Action/Action Creator

So the events have been fired off, now what? Just as in Redux, you have to create what we call `actions`. An action in Redux typically contains a `type` and a `payload`. The `type` will contain a description of the change to take place, while the `payload` will contain what will be changed.

In Re-Frame, you are sending off a simliar `action` if you will. You dispatch a vector that will contain the `name` of the event as well as the payload that will be required. For example

```
[:update-name "Josh"]
```

Which will tell Re-Frame, dispatch an event named `update-name` with string `Josh`.

### Domino 3 - Effect Handling

> React/Redux - Reducers

So now that these have been dispatched into the Redux/Re-Frame world, now what? These are merely descriptions, now we need actual changes to be made or what is the point? In Re-Frame, you write effect handlers which will be on the lookout for names of the events that we named as the `type` or `name` of action/effect in the previous domino.

In Redux, you will write reducers, which perform in a very similar manner. They receive all actions and will switch on the actions types and when there is one that they are looking for, they will grab that payload and perform the prescribed update of the app state.

In both cases, this is the domino where the changes are propagated and our app state is updated.

### Domino 4 - Query

> React/Redux - Mapping State to Props

So our app state has been updated, what next? The architecture of Re-Frame and Redux are the same in that the view is a function of the state. Once the state is changed, the view will then change.

In React/Redux, you will use most likely the `react-redux` library to write a function `mapStateToProps`, which will, as described map the current state of Redux to the props in your component. The way this works is that it subscribes and listens to updates in the state of redux and updates the props when this happens.

In Re-Frame, you again will do something vary similar and write `subscriptions` which will listen to parts of the Re-Frame state and update the view when the data it is subscribed to is updated.

### Domino 5 - View

> React/Redux - JSX

This is again, very simliar. You might even see a pattern! In React/Redux, we write React component using JSX which React will use to create DOM elements.

In Re-Frame, we use Reagent to write React components, which, as you probably guessed, will create React components.

### Domino 6 - DOM

> React/Redux - DOM

VOILA!!

Luckily for us, just like it mentions in the Re-Frame docs, this is handled by React / Reagent. It will take the JSX or Clojurscript we wrote and render it to the virtual dom.

### In Closing

We made it! As you can see, you can see how closely you can map Re-Frame to React/Redux. Now, you may be asking, why would I switch? Well, I for one can say the API for Re-Frame is much smaller, saner and easier to reason about. You also have the benefit of using Clojurescript (WHICH IS AMAZING), and when you are doing immutable state changes make it an absolute joy. The community is also extraordinary. I think that you will really enjoy writing Reagent. I much prefer the Hiccup syntax to writing JSX.

And one of my favorite parts, the tooling is incredible! You get to use figwheel, which if you haven't used it before will give you a development experience that is truly the cats pajamas. You really feel in tune when developing, at least I do. 10x is excellent as far as visibility into your application and the inner workings of Re-Frame and many other utilities that you will find along your way.

I dare you once using a repl for front end development not want to use it exclusively.

Thanks for reading, hope you enjoy Clojurescript and Re-Frame as much as I do.

Any questions/corrections please let me know!
