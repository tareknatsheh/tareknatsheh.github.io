---
layout: post
title:  "Create a CI/CD workflow for Unity Android builds using Github Actions"
date:   2023-10-20
categories: how-to
---

# {{ page.title }}

I've followed the instructions here [GameCI](https://game.ci/docs/github/getting-started){:target="_blank"}

Here is my final `.yaml` file

{% highlight yaml  %}

name: Test and build the sample game

on:
  workflow_dispatch:

env:
  UNITY_LICENSE: ${{ secrets.UNITY_LICENSE }}
  UNITY_EMAIL: ${{ secrets.UNITY_EMAIL }}
  UNITY_PASSWORD: ${{ secrets.UNITY_PASSWORD }}
  githubToken: ${{ secrets.GITHUB_TOKEN }}

jobs:
    checkLicense:
        name: Check for the Unity license ☑️
        runs-on: ubuntu-latest
        steps:
            -   name: Fail - No license ☠️
                if: ${{ '{{' }} !startsWith(env.UNITY_LICENSE, '<') }}
                run: exit 1

{% endhighlight %}