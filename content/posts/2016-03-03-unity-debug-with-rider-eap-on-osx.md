---
title: Unity Debug with Rider-EAP On OSX
author: Leroy Shirto
date: 2016-03-03T00:08:53+00:00
tags:
  - Misc

---
So Project Rider recently went EAP and I was eager to get it running on my Mac to see if it would be a viable replacement to Monodevelop or VSCode for Unity Development. Rider does not currently have Unity Debuging out of the box, [VSCode][1] is able to so I did some digging and was able to get Rider to connect to Unity and debug. It was easier than I thought it would be to get debugging in Rider. By creating a new debug configuration in Rider and setting the the port Unity was listening on I am able to set breakpoints and debug my Unity Projects.

To get this working start by creating a debug run configuration in Rider.

Open a terminal while Unity is running a project and run the command

`lsof -c /^Unity$/ -i 4tcp -a`

You should see the first line of output with something similar to

`TCP *:56197 (LISTEN)`

Set this port in your Rider debug configuration and save.

Set a breakpoint in Rider then run the project in Unity.

Switch back to rider and start the debugger. It should connect and stop when it reaches your breakpoint. You can then step through the code as normal.

The downside is that the port changes every time Unity starts. VSCode gets over this by running an Editor Plugin which runs command above whenever Unity starts and writing it to VSCodes launch file. My next step is trying to find a way to do the same for Rider.

<a 
    href="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.05.18.png"
    rel="lightbox[175]" 
    rel="attachment wp-att-178" 
    title="Unity Debug with Rider-EAP On OSX">
        <img 
            src="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.05.18.png" 
            alt="Screen Shot 2016-03-03 at 00.05.18" 
            width="660" 
            height="420" 
            srcset="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.05.18-300x191.png 300w, /images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.05.18-768x488.png 768w, /images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.05.18-1024x651.png 1024w" 
            sizes="(max-width: 660px) 100vw, 660px" />
</a>

<a href="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.04.59.png" rel="lightbox[175]" rel="attachment wp-att-180" title="Unity Debug with Rider-EAP On OSX"><img src="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.04.59-1024x554.png" alt="Debugging In Rider" width="660" height="357" class="aligncenter size-large wp-image-180" srcset="/images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.04.59-300x162.png 300w, /images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.04.59-768x415.png 768w, /images/uploads/2016/03/Screen-Shot-2016-03-03-at-00.04.59-1024x554.png 1024w" sizes="(max-width: 660px) 100vw, 660px" /></a>

Thanks go to this [VSCode Integration][2] project which helped me work out what port the Unity debugger was listening on.

 [1]: https://code.visualstudio.com/Docs/runtimes/unity
 [2]: https://github.com/dotBunny/VSCode
