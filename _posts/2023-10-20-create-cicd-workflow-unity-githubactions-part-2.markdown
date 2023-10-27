---
layout: post
title:  "Part 2 - Deploy Unity app to Google Play using Github Actions CI/CD workflow"
date:   2023-10-27
categories: how-to
---

### Here are the secrets you’ll need to have for this part:

The following are relevant to the Unity project, and should be the same as what you set in **Build settings > Player Settings > Publishing Settings**

When you create a new keystore, you will need to set a password, and alias and a password for the alias (pro tip: use the same password and you’ll thank me later)

- **ANDROID_KEYSTORE_PASS**: password of the keystore
- **ANDROID_KEYALIAS_NAME**: name of the alias
- **ANDROID_KEYALIAS_PASS**: password of the alias (as mentioned, just make the same as the password for the keystore)
- **ANDROID_KEYSTORE_BASE64**: ok this guy needs some PowerShell magic, this is how you generate it:

Open PowerShell and navigate to the place where you have the .keystore file

Run this:
`[convert]::ToBase64String((Get-Content -path "user.keystore" -Encoding byte))`

Copy the generated stuff and past it in ANDROID_KEYSTORE_BASE64

- **ANDROID_PACKAGE_NAME**: It’s the `com.yourcompany.yourapp` check the **Build settings > Player Settings > Other Settings > Package Name**  in Unity to get the correct value.

---

- **GOOGLE_PLAY_KEY_FILE**: PAINNN! but it’s fine, here is how to get it:

Here are the instructions: <https://game.ci/docs/github/deployment/android#2-create-a-google-play-service-account>

But honestly the documentation is not enough and it’s a bit confusing.

<aside>
💡 // TODO: document how you did it here

</aside>


---

- **UNITY_LICENSE**: To get this guy, first run this workflow in github actions: .github/workflows/activation.yml

And follow instructions here: <https://game.ci/docs/github/activation>

And pay extra attention to this:

![unity license issue image](/assets/images/unity-licence-issue.png){: width="500" }

Now you should be ready to run and release to Android store for your Internal Testers!