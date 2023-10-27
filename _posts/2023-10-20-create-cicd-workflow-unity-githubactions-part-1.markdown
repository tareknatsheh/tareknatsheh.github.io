---
layout: post
title:  "Part 1 - Build a Unity .apk using Github Actions CI/CD workflow"
date:   2023-10-20
categories: how-to
---

I've followed the instructions here [GameCI](https://game.ci/docs/github/getting-started){:target="_blank"}

But things were not as straight forward as I've hoped, so I will document here the way I’ve automated the build and deployment to “internal testing” in **google play console** using **Github Actions** CI/CD tool.

My approach will be to first start with a minimal Unity game ready to be used.
The challenging and time consuming part will be the environment variables (or the "secrets" as referred to in Github Actions)

**Prerequisites:**

- Fork or clone this minimal Unity test project [CICD-tester repo](https://github.com/sarab5000/cicd-tester/tree/master)

### The Github Actions workflow

All of the workflows that contain the instructions for Github Actions should be in this directory:

`<root>/.github/workflows`

it should has a ``.yml`` or ``.yaml`` extension, and you can call it whatever you want, I’ll call it main.yml, so you'll have it like this:

`<root>/.github/workflows/main.yml`


First, you will need some “secrets”  🤫

In your copy of the repo in Github go to **Settings > Secrets and Variables > Actions**



### Here is the list of secrets you’ll need to have for this part:

- **UNITY_LICENSE**: To get this guy, first run this workflow in github actions: .github/workflows/activation.yml

And follow instructions here: <https://game.ci/docs/github/activation>

And pay extra attention to this:

![unity license issue image](/assets/images/unity-licence-issue.png){: width="500" }

---

Create a new Unity Account, and use email and password, DO NOT login using google/github or other login methods:

- **UNITY_EMAIL**
- **UNITY_PASSWORD**

---

Now you are done with the CI (continuous integration) part!

Do you want to also automate the deployment to Google Play store? yes? oh.. ok, then check out [PART 2](/how-to/2023/10/27/create-cicd-workflow-unity-githubactions-part-2.html)