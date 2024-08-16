---
layout: post
title:  "New Unity project set up"
date:   2023-08-16
categories: unity
tags: unity
---

When I create a new Unity project there are a couple of standard steps I take to ensure that everything is organised.

## Assets Structure ##

The first thing to do is to set up the folder structure. Under *Assets* I create a new folder with the name of my game or app. I immediately move any file that exists there and under it I create all the folders I intend to use eg. *Scripts*, *Scenes*, *Prefabs* etc. The reason I'm doing this is because the root folder may be filled up by other assets and I want to have a clear understanding of what I've created for the project versus what I imported into it from another source.

On a similar note this is one of the reasons I prefer adding a new assets from Unity Package Manager. It's hidden under the packages directory and doesn't mess with the rest of the *Assets*. Another reason is that it keeps its own Assembly Definition that helps organising modules inside the code. I'll get to that as well.


## Root Namespace ##

Then I set up project settings. The name of the app or at least a temporary one, the name of the company and before I start creating my scripts the root namespace. In Project Settings, in the Editor tab I set the Root namespace to *com.CompanyName.ProductName*. So now for every new C# script I create inside Unity the namespace is already set due to that. Setting namespaces is helpful to understand in which module in your code a class belongs.

When I see the namespace *com.CompanyName.ProductName.CSVExport* I understand that the code belonging in there is used to export something to CSV and in there I may have classes like *ExportItem*, *ExportAll*, *ExportHighest* thus distinguishing what I want to use. Additionally by using namespaces my class names won't conflict with classes from other packages I import. If I find two InputHandler classes and one belongs to a namespace that ends in *CSVImport* that probably doesn't have to do with a mouse or keyboard.

## Git ##

For every new project I have I almost immediately create a new remote git repository and push it there. There are a couple of advantages that a remote repository offers. First of all **Backup**! I feel safe that whatever happens to my system I can always find my project there. Secondly, git keeps history of changes. Every commit offers a diff that I can look at and find what changed. Additionally, editors like [JetBrains Rider](https://www.jetbrains.com/rider/) offer a system that labels which git user has created a method and also indicate when was the latest change or helpfully use Blame to see who changed which line. This is helpful in case a new bug surfaces.

The root directory becomes the one that includes the Assets folder. I try to keep that directory clean and only have there the Packages and ProjectSettings folders along with the .gitignore and a README.md.

## Unity Package Manager ##
https://docs.unity3d.com/Manual/upm-ui-actions.html

## Assembly Definitions ##