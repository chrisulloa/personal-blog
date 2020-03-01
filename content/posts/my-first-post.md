---
author: "Christian Gonzalez"
categories: [ "Development" ]
title: "Speeding up GraphQL query execution"
description: "Improving performance of a GraphQL API written in Clojure with walmartlabs/lacinia"
date: "2020-02-29T17:49:40-08:00"
tags: [
 "clojure",
 "graphql"
]
---

Improving the performance of a Clojure GraphQL API built with [Lacinia](https://github.com/walmartlabs/lacinia) <!--more-->

## Background
I am currently helping maintain a GraphQL service that aggregates data from different services and makes it consumable for a mobile app. A major hurdle for any backend developer working with microservices is juggling data retrieval from other downstream services. There's also the added responsibility of ensuring reasonable loading times so that users have a good, responsive experience while using your app.

## Improving performance
One of the easiest ways to improve performance of your GraphQL service is to manage your network calls smartly. That means cleaning up all those blocking network calls in your field resolvers.

## Asynchronous Execution
One of the more interesting things about Lacinia is its support for [asynchronous field resolvers](https://github.com/walmartlabs/lacinia/blob/master/docs/resolve/async.rst). Allowing query execution to happen in parallel can be very useful for speeding up a GraphQL API.
