# How to enable Chrome Autoplay? 

Having trouble **enabling** Chrome autoplay? Here's a solution

## Introduction

Autoplay is beneficial for some applications. Say, you are on YouTube and click on a video. Chance is very high that you want to play the video so that configuring the site to play videos automatically may make sense.

Google introduced a new flag in Chrome 61 which gives users of the web browser control over the browser's autoplay behavior. However, many user report not being albe to find the autoplay policy. Google has presumably removed this feature from Google Chrome, as many people are unable to find this policy. (photo below)

![Google Chrome Autoplay Policy](https://www.ghacks.net/wp-content/uploads/2018/02/chrome-autoplay-policy.jpg)




I found my self not being able to find the autoplay policy by browsing to chrome://flags/#autoplay-policy. Like suggested in multiple online forums. I found all answers out to date and had a hard time finding an answer to my question: *How can I **enable** autoplay so my videos automatically start playing* as this was a requirement for my kiosk application.


## The autoplay policy


By default the autoplay policy is set to *User gesture is required -- Users need to interact with the document for video or audio sources to start playing automatically.* 

THe autoplay policy has three different options: 

* **Default** -- Document user activation is required -- Users need to interact with the document before audio or video content is played automatically.
* No user gesture is required -- Users don't need to interact with the document for video or audio sources to start playing automatically.
* User gesture is required for cross-origin iFrames -- Same as "no user gesture is required" but only for same-origin media content. Audio or video content loaded from other sites require user interaction.


## Changing the autoplay policy

If you're lucky you're able to set the autoplay policy by navigating to chrome://flags/#autoplay-policy in your chrome broswer.


However, I found that I and other people were unable to locate the autoplay policy in Google Chrome, and found it to be presumably removed from the flags list in Google Chrome. 


My kiosk application launches from a batch script, adding the following argument to my code set the autoplay policy to _No user gesture is required -- Users don't need to interact with the document for video or audio sources to start playing automatically._ This suited me best as I needed the page to autoplay the videos displayed. 

I added the following argument to my line. 

```--autoplay-policy=no-user-gesture-required```

Which now looks like this: 

```
cd "\Program Files (x86)\Google\Chrome\Application"

Timeout 3

chrome.exe --kiosk --autoplay-policy=no-user-gesture-required https://www.google.com/

```

You might be wondering what some of the arguments actually mean, so I'll explain them below. 


* The `--kiosk` makes Chrome start in fullscreen mode. 
* The `--autoplay-policy=no-user-gesture-required` Makes Chrome set the autoplay-policy to `no-user-gesture-required`. Just like we wanted. 
* The webaddress `https://www.google.com/` Just makes Chrome open the specified web address. 

The rest should be pretty much self explanatory. 

More information on the autoplay policy can be found in Google's help article (which I found not to be helpfull at all): https://developers.google.com/web/updates/2017/09/autoplay-policy-changes

## License

This guide is licensed under the MIT license, you can view the license here: https://github.com/Hugo22O/chrome-autoplay/blob/master/LICENSE





