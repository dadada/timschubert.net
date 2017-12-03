---
layout: post
title:  "My $HOME"
date:   2017-11-18 00:00 +0100
categories: filesystem projects
---
Recently I came across a blog posting titled "[$HOME, sweet $HOME](https://morr.cc/home-sweet-home/)", where [@blinry](https://morr.cc/) advocates structuring your `$HOME` directory based on projects and their activity.
Afterward reading this I felt inspired to finally have a look at the mess I made of my `$HOME` in the last couple of years.

A few things about my old `$HOME`:
- ``Documents`` contained basically everything I had accumulated during the last years besides music, videos, pictures and version controlled source code.
- ``projects`` just contained one gigantic folder of all projects under version control that I ever worked on. Even with TAB completion, this still has been still hard to navigate at times
- the rest was based on the default [xdg-user-dirs](https://freedesktop.org/wiki/Software/xdg-user-dirs/)

If you rigorously applied sorting yout files by file type like the default XDG directories suggest, files from one project may be scattered across many different directories.
At the same time, for some directories such as `~/Documents/study/` I had a usable system for cataloging everything.
One problem with my system still was that if I started a project in the context of a course in `study`, it would be unclear whether to place it in `~/projects` or into the directory of the course.

So my goal for the new `$HOME` was to have a clean directory structure where:
 - it is obvious where to place new files so they can be found
 - paths do not become too long to type out
 - the directory structure can be adapted to how I work while I keep using it

A quick tour of my new `$HOME`:

| directory  | usage                            | structure              |
| :--------- | :------------------------------- | :---------------       |
| lib        | immutable files                  | media-type/            |
| src        | stores all projects              | project-name/          |
| tag        | stores links to projects         | tag-name/project-name/ |
| tmp        | unsorted files, experiments      | (chaotic)              |
| usr        | place for installing software    | like /usr              |

# The project directory

```shell
$ ls ~/src
hello-world fizzbuzz example1
```

All of my projects are stored in `src`.
I use a flat directory structure, where every project has its own subdirectory based on its name.
Projects can become part of one or more larger contexts through the use of tags. 

# Tags

Tags are stored in `tag`.
Each tag is a directory with the name of the tag that stores symbolic links to parts of the project.
The fact that both `src` and `lib` have a simple structure where directories do not move around much helps not breaking links after they are created.

```shell
$ cd tag
$ mkdir -p course1/examples
$ ln -s ~/src/example1 course1/examples/
$ ln -s ~/lib/courses/course1 course1/material
$ rm -r course1
```

I create new tags for various reasons, but mostly one for each larger context (e.g. work, hobbies, admin, thesis, courseXY) and some more for tracking project activity.
There are four different tags in my `tag`s directory right now for tracking project activity:

| directory  | usage                            | structure        | change files   |
| :--------- | :------------------------------- | :--------------- | :------------: |
| permanent  | links to permanent projects      | project-name/    | yes            |
| active     | links to active projects         | project-name/    | yes            |
| hold       | links to inactive projects       | project-name/    | no             |
| dead       | links to dead projects           | project-name/    | no             |

# The Archive

The contents of every file in `lib` will not change after it is first moved there.
Files that where created from a project in `src` like documents, pictures and recordings will sometimes move here.
Everything that collects in `tmp` and I deem worth keeping will eventually be placed sorted into `lib`.
There are quite a few subdirectories that each more or less corresponds to the type of media they contain.
Each subdirectory uses a different indexing system based on what appears to work best for the media type.

The material for each course in `courses` is mostly self-contained and having everything for one course together in one place is more useable.
So videos of lectures, notes and worksheet solutions will all be munched together in there.

```shell
$ ls ~/lib
backups  books	documents  games  courses  music  pictures  videos
```

Organizing my personal little library based on a cataloging system still remains an item on my TODO list for when I get really bored.

# Workflow

![Basically this]({{ "/blog/assets/home.svg"}})
