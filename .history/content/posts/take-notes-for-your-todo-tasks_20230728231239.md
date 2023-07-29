---
title: "Take Notes for Your Todo Tasks"
date: 2023-07-25T08:38:58+08:00
---

Nowadays TODO management apps are everywhere. From giant tech companies to emerging individual developers, everyone is creating TODO apps. Even some programming tutorials are about how to create a TODO app. The reason behind its popularity is obvious: almost everyone needs a TODO app. But unfortunately, only a small part of people knows how to manage TODO tasks most efficiently.

Do you know how to use a TODO app? Yes, of course, you do. Just open a TODO app and add some TODO tasks to it. When one of them is finished, simply mark them as finished by clicking on the little square before each TODO item, it's that simple, right? Yes, it could be that simple, you can manage your TODO tasks successfully in this way. But in my view, you missed an important part: you didn't note down the process of how you finish each TODO task.

You may have indulged deeply in your usual task-management process, to the extent that you may not even realize the note-taking part is important. So let me give you some examples. Suppose you created the following TODO task that you need to finish today:

- [ ] Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.

After several hours of debugging and coding, you finally found the reason and fixed the problem. With fulfillment, you opened your TODO app again and marked it as finished. "Good job!" You said to yourself: "Nothing is wrong here".

But really? In my view, you missed an important part: take notes for the process of solving the problem. You should write down how you find the reason for slowness, how you fixed it, and how to avoid similar problems in the future. What's more, the note is not taken after you solved the problem, it's taken **along** the process of solving it. Only in that way can you benefit from the notes most.

# Advantages of Taking Notes for TODO Tasks

Why should I take notes for my TODO tasks? Isn't it enough to just finish the task in any way I want? After all, the most important thing is that I've completed the task, right? Well, maybe, but if you don't take notes for those tasks, you may miss something. There are some clear benefits for taking notes for TODO tasks, to name a few:

1. You may encounter similar problems in the future. When that happens, you can refer to the current note as a problem-solving template.
2. You may find some of those notes useful in the future, even if you won't encounter similar problems again. For example, when solving the problem, you may learn some knowledge about CPU. You can just note them down. When you want to look up something you've learned about CPU several months later, you can search for "CPU" in the notes, and voila! That knowledge, along with the context - the slowness bug - pops up in front of you. Context-aware resources can help you learn more quickly and deeply.
3. The notes can guide you through solving the problem. This is the **MOST IMPORTANT** reason why you should take notes for your TODO task. As an old saying goes:

   > Writing is not the artifact of thinking, it's the actual thinking process.

   I believe you won't solve the slowness problem immediately, at least not every time. You have to first reproduce the problem, then monitor all the relevant indicators to see if anything is abnormal. You may also need to adjust some parameters to see what happens. You can write all of them in the notes, and let the notes guide you through solving the problem. It's just like solving a mathematical problem. Some problems are hard to solve. Whenever an idea comes to your mind, you need to write them down in a notebook, fiddle around with them for a while, and maybe after writing enough information can you find the right way to solve it.

That being said, do notice that some TODO tasks are not suitable for taking notes. Like "Remember to take out the garbage first thing in the morning", or "Finish the code of the sharing functionality for my app". The former is too simple to note anything down, the latter is more about coding, which is usually done in an IDE, not much to be written down in the notes.

# Let's take an example

Now suppose you want to fix the problem mentioned above:

> Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.

To do that, you first created a TODO task:

<div class="callout">
    <h6>TODO</h6>
    <p><b>Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.</b></p>
</div>

After creating the task, we are ready to get down to it. As everyone knows, the first thing we need to do when solving a problem would be to try reproducing it. So let's add the following notes under the TODO task **before** doing anything.

<div class="callout">
    <h6>TODO</h6>
    <p>Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.</p>
    <h6>NOTES</h6>
    <p><b>First let's try reproducing the issue by following the user's guide:</b></p>
    <ol>
        <li><b>Start the app.</b></li>
        <li><b>Click on the "START" button to start processing.</b></li>
        <li><b>Observe the duration to be longer than expected.</b></li>
    </ol>
</div>

After writing those notes, you started the app, clicked on the button, and found the duration to be 30 seconds, longer than the expected 3 seconds. You also write that in the notes

<div class="callout">
    <h6>TODO</h6>
    <p>Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.</p>
    <h6>NOTES</h6>
    <p>First let's try reproducing the issue by following the user's guide:</p>
    <ol>
        <li>Start the app.</li>
        <li>Click on the "START" button to start processing.</li>
        <li>Observe the duration to be longer than expected.</li>
    </ol>
    <p><b>I've reproduced the issue, the duration is 30 seconds, longer than the expected 3 seconds.</b></p>
</div>

So what's the culprit? You remembered that the number of the app's users has increased a lot in the past few days, but the number of backend servers for the app hasn't changed for months. Maybe these servers cannot support that many users' requests? That's possible. To verify the assumption, we need to check the servers' logs to see if the servers' duration has increased. As usual, add the action and the corresponding log to the notes:

<div class="callout">
    <h6>TODO</h6>
    <p>Some users report that my app sometimes runs slow, I need to pinpoint the reason and fix it.</p>
    <h6>NOTES</h6>
    <p>First let's try reproducing the issue by following the user's guide:</p>
    <ol>
        <li>Start the app.</li>
        <li>Click on the "START" button to start processing.</li>
        <li>Observe the duration to be longer than expected.</li>
    </ol>
    <p>I've reproduced the issue, the duration is 30 seconds, longer than the expected 3 seconds.</p>
    <p><b>Maybe it's because the backend servers are overloaded. Need to check the servers' logs first.</b></p>
    <p><b>The following log is taken from the server with IP 192.168.10.50:</b></p>
    <ol>
    <b><li>Finished processing user Joey's request, duration: 28 seconds.</li></b>
    <b><li>Finished processing user Rachel's request, duration: 32 seconds.</li></b>
    </ol>
</div>

So the servers' request time has indeed increased, the next step would be to check the servers' various indicators, like CPU, memory, load, etc. You should also append this information to the notes, you get the idea, I won't go into details anymore. The writing process can guide you through fixing the issue. What's more, you may find the notes useful someday in the future, I cannot tell you how many times I got valuable information about the past in previous TODO notes!

# As for Note-Taking, What Counts as a Good TODO App/Scheme?

Now you know why TODO notes are important and how to take them, the next question would be which TODO app we should use. But before making a choice, we may need to consider what features we want from a TODO app in terms of note-taking. In my view, three features are the most important:

1. **It has to support adding notes for each TODO task.** Since we are talking about notes, this feature is an obvious one.
2. **The notes should support text formatting like italics, code blocks, etc.** This is because our notes could be complicated sometimes. We may need to record code blocks, headers, quotes, etc in the notes to make it easy to understand. It would be hard to take long notes without the feature.
3. **The whole TODO list should be stored in - or at least can be imported and exported to - a plain text format**. By plain text format, I mean Markdown, Org Mode, etc. They are powerful enough to store multiple formats in a single text file. To be honest, this is not a must-have feature, but it's nice to have it. When your TODO list is stored in a plain text format, you can search for/edit anything you want with any editor, you will not be bound to a certain vendor product.

# How Does Each TODO App Do in Terms of Note-Taking?

Now we have three requirements for TODO apps, let's take a look at some well-known TODO apps and see how each of them does in this regard.

## Microsoft To Do

One of the most famous TODO apps is [Microsoft To Do](https://todo.microsoft.com/tasks/).

![Notes in Microsoft To Do](/images/microsoft-to-do-notes.png)

Microsoft To Do allows you to take notes for each task at the right bottom part of the UI (Found the "Add Note" part in the image above?). That's enough for most people, but the notes can only be plain text, it doesn't support quotes, code blocks, etc. So it's not the perfect solution. Maybe Microsoft doesn't want the app to be complicated. If the user needs to take notes with formatting elements (heading, bulleted lists), he/she can do this in other apps. Besides, you can only see/edit TODO tasks inside the app, there is no way to export the TODO list to a text file. So Microsoft To Do only supports the first feature.

Score: ★★★☆☆

## Todoist

Todoist to also a famous TODO management, it seems to have more features than Microsoft To Do. You can try creating a TODO task and adding some notes to it, then you will immediately realize that the app surely supports the first two features - It supports Markdown in its TODO description/comments and renders it perfectly:

![Todoist](/images/todoist.png)

It doesn't support importing/exporting the TODO list to a text file, but it supports the first two features perfectly.

Score: ★★★★☆

# Agenda

[Agenda](https://agenda.com/) is built based on the idea that notes and dates should be combined together, which is closely aligned with ours. Strictly speaking, it's not a TODO app, at least not a traditional one, the official website describes the app as *Notes meets Calendar*. But since it can set a date for a block of notes, you can use it as a TODO app with notes emphasized.

![Agenda](/images/agenda.png)

Agenda has a premium feature that supports exporting the notes into markdown files. I haven't bought Agenda so I don't know how it does. But I guess it should work. So in summary, Agenda supports all the three features we mentioned above, which seems to be a great app worth trying.

Score: ★★★★☆

## Emacs With Org Mode

This is my favorite one. But a lot of people don't know Emacs or Org Mode at all, maybe that's because it's a niche product mainly used by programmers.

First of all, Emacs and Org Mode are two separate things. Emacs is a highly-customizable text editor, just like Vim. While Org Mode is a markup language, just like Markdown. It's not as popular as Markdown so a lot of people don't know it. Theoretically, you can edit Org Mode documents with any editor, but most people choose Emacs because it has excellent support for Org Mode.

Org Mode has many attractive features that are not available in Markdown. Since we are talking about notes and TODO tasks, I'll only pick relevant features in Org Mode. In Markdown, we add a header with `#`. That's similar in Org Mode, only that we use `*` instead of `#`. What's more, You can add the `TODO` keyword after `*` in Org Mode to make it a TODO header, here is an example:

```org
* TODO Install Emacs in macOS

** DONE Install vanilla Emacs

We can use ~brew~ to install vanilla Emacs, the command is as follows[fn:1]:

#+begin_src sh
brew update
brew install emacs
#+end_src

** TODO Install Doom Emacs

Run the following command to install Doom Emacs[fn:2]:

#+begin_src sh
git clone --depth 1 https://github.com/doomemacs/doomemacs ~/.config/emacs
~/.config/emacs/bin/doom install
#+end_src

* Footnotes

[fn:1] [[https://orgmode.org/org.html#Installation][The official Org Mode website]]

[fn:2] [[https://github.com/doomemacs/doomemacs][The Doom Emacs git repository]]
```

Here is the rendering effect (You may get a different rendering depending on your Emacs configurations):

![Org Mode rendering](/images/org-mode-rendering.png)

It's just like Markdown, only using a different set of symbols. I won't try to tell you all the meanings of those symbols, but you can guess. Here we created a top TODO task, which is to install `Emacs` in macOS. When we added this TODO task, we may know nothing about how to do that. After some investigations, we may find that we need to install two parts, the first is vanilla Emacs, and the second is Doom Emacs. Again, you don't need to know what they are, the point is that we figured out we need to install two parts, so we created two sub-tasks under the main task. Then we list all the commands we need to run to install them. We can also attach the result to the notes (By the way, Emacs can run those commands directly in the notes!) so that whenever any error occurs, the result can be taken as a good reference for pinpointing the reason.

In the end, when we finished the first sub-task, we change the `TODO` keyword to `DONE`, just like we change `- [ ]` to `- [X]` in Markdown. It not only removes the TODO task from the TODO list but also gives us "a dose of dopamine" for finishing the task.

Although Org Mode is great in many ways, few apps support Org Mode, and Emacs is almost the only app that supports all the features of Org Mode. Yes, you can edit Org Mode files in any editor you want. But if you want to do something with TODO tasks in Org Mode files, like checking TODO tasks scheduled at a certain date, or checking all the TODO tasks with the highest priority, Emacs might be your only option. And here comes its biggest problem: Emacs is not that easy to learn, even for professional programmers. That is a huge obstacle for ordinary people.

Emacs with Org Mode supports all the three features mentioned above, but it's hard to learn, which is a deal killer for most people, so I'll only give it three stars, although it's my favorite.

Score: ★★★☆☆

# Now What Should I Choose?

There are many TODO apps nowadays, and most of them support adding notes, only the degree of support varies. You may ask which one to choose, and my answer to that question would be: just pick one, don't hesitate. In my view, the biggest problem is not that most TODO apps don't have great support for notes. The biggest problem is that most people don't know they should take notes for their TODO tasks. So just pick one TODO app, and start taking your TODO notes from today!