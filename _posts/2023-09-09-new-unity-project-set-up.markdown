---
layout: post
title:  "New Unity project set up"
date:   2023-09-09
categories: unity
tags: unity
---

When I create a new Unity project there are a couple of standard steps I take to ensure that everything is organised.

## Assets Structure ##

![Project structure](/docs/assets/images/project_structure.png)

The first thing to do is to set up the folder structure. Under *Assets* I create a new folder with the name of my game or app. I immediately move any file that exists there and under it, I make all the folders I intend to use eg. *Scripts*, *Scenes*, *Prefabs* etc. The reason I'm doing this is because the root folder may be filled up by other assets and I want to have a clear understanding of what I've created for the project versus what I imported into it from another source.

On a similar note, this is one of the reasons I prefer adding new assets from Unity Package Manager. It's hidden under the packages directory and doesn't mess with the rest of the *Assets*. Another reason is that it keeps its own Assembly Definition that helps organise modules inside the code. I'll get to that as well.


## Root Namespace ##

![Player settings](/docs/assets/images/player-settings.png)

Then I set up project and player settings. The name of the app or at least a temporary one, the name of the company and before I start creating my scripts the root namespace. In Project Settings, in the Editor tab, I set the Root namespace to *com.CompanyName.ProductName*. So now for every new C# script I create inside Unity, the namespace is already set due to that. Setting namespaces is helpful in understanding which module in your code a class belongs to.

![Root namespace](/docs/assets/images/root-namespace.png)

When I see the namespace *com.CompanyName.ProductName.CSVExport* I understand that the code belonging in there is used to export something to CSV and in there I may have classes like *ExportItem*, *ExportAll*, *ExportHighest* thus distinguishing what I want to use. Additionally, using namespaces my class names won't conflict with classes from other packages I import. If I find two InputHandler classes and one belongs to a namespace that ends in *CSVImport* that probably doesn't have to do with a mouse or keyboard.

## Git ##

For every new project I have I almost immediately create a new remote git repository and push it there. A remote repository offers a couple of advantages. First of all **Backup**! I feel safe that whatever happens to my system I can always find my project there. Secondly, git keeps a history of changes. Every commit offers a diff that I can look at and find what changed. Additionally, editors like [JetBrains Rider](https://www.jetbrains.com/rider/) offer a system that labels which git user has created a method and also indicates when the latest change or helpfully use Blame to see who changed which line. This is helpful in case a new bug surfaces.

![Rider git](/docs/assets/images/rider-git.png)

The root directory becomes the one that includes the Assets folder. I try to keep that directory clean and only have there the Packages and ProjectSettings folders along with the .gitignore and a README.md.

## Unity Package Manager ##
There is something inherently great about using UPM assets
* The project remains organised as the upm packages are left on their own without interfering with the project structure. This makes them also easy to remove without leaving traces!
* They promote good coding practices as they don't let the users edit their content (not permanently at least)
* They come up with versioning and usually a changelog.
* They also come up with assembly definitions


## Assembly Definitions ##
This is a bit advanced and can be confusing to new users. It's also unnecessary for small projects and can be postponed early in development but it's easy to forget it altogether until you already experience spaghetti code issues. [Unity's documentation](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html) explains it adequately.

> An assembly is a C# code library that contains the compiled classes and structs that are defined by your scripts and which also define references to other assemblies.

> By default, Unity compiles almost all of your game scripts into the predefined assembly, Assembly-CSharp.dll

By defining assemblies the code is split into *modules*. In big projects the compile time can be reduced as Unity will only compile all the scripts of the assembly instead of every script in the project. Additionally, they promote good coding practices and prevent cyclical references.

If you already know the future structure of your project you should take care of splitting it into big modules and creating assembly definitions early on. Or maybe you should give Unity Packages a go by turning some modules into unity packages.