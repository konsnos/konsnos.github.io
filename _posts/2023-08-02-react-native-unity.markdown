---
layout: post
title:  "React Native Unity iOS notes"
date:   2023-08-01
categories: unity
tags: unity, react-native
---

These are a couple of notes from my adventures with integrating Unity with React-native.

In general I had a hard time implementing the integration. Harder than what I had with Flutter.

For the integration I used [azesmway/react-native-unity](https://github.com/azesmway/react-native-unity) plug-in. As hard as I tried I couldn't get it to work and I was confused with all the different ways of creating a new react-native app.

In the end I followed the instructions of [dev.family's blog](https://dev.family/blog/article/integrating-unity-code-into-react-native). In the end of the post there were a couple of links from the sample app they made which I cloned. And their repo worked! From that I understood how the folder structure worked in the plug-in. To build the framework I had to select it from XCode and run it.

[UnityFramework build](images/build_framework.png)

After the build find it from the DerivedData folder and copy it to `/unity/builds/ios` path. In that path I added another framework I needed to include, although I also had to add that in XCode as well. So placing it inside the folder isn't required but helps me organise stuff.

After a couple of tests in their Unity sample I embedded my own Unity app and it worked splendidly. However, some commands where different in my case. First of all sometimes `npm install` worked and other `yarn` did. Hopefully with one of those commands the react-native packages were installed each time I had to reset the project to try something new.

During my tests I had to clear the pods so my go-to command was `rm -rf ios/Pods && rm -f ios/Podfile.lock && npx pod-install` instead.

Finally, I ran Metro in terminal and the command that worked for me to run it to device was `yarn run ios --device "Konstantinos’s iPhone 12"`. The installation worked but the app never launched so I didn't have the opportunity to debug it. To do that I ran the build from XCode.

Communication back and forth worked so I'm happy with the integration. As a side note the tools I used, had Chrome selected by default for some reason I didn't understand. After a lot of failures I installed it to try it out, and it seems that some kind of debugging works there. Thankfully it wasn't required to build the app and I ditched it as soon as I could.

That's it! Any performance drop was not immediately visible and I didn't stress test it. Flutter was more straightforward from my experience.