# Identifying Potentially Malicious Applications

This is an investigation on whether developer-created apps within web applications are potentially dangerous to users and web-app companies. 
This deep dive was done using Bigquery and some visualizations have been generated in the visualizations file.




Assumptions/Flag App If Rules I needed to make to start this deep dive

1. If a developer has a warning reason listed on their account
    1. in this case, a dev with a warning_reason has reasonable suspicion to make bots/apps that are harmful/malicious and worth flagging for further investigation. 
2. If an avatar hash or description is null
    1. If someone creates an app and the icon is blank it raises some red flags: why make an app with no icon (unless it’s intended to be made quickly and act maliciously)?
    2. Similar to the normal avatar hash, if a description is not made (and this is something that cannot be changed after registration) then it doesn't make sense why a genuine developer would leave an app description.
3. If guild count is low 
    1. If this app has a low guild count it’s probably not available to many users or not joined to many (meaning it could be serving as a malicious copy)
4. If the app sounds similar to another existing app 
    1. The situation stated problems with apps that had similar names which posed a threat. Using the Soundex function in google biquery, I am able to discover apps with similar phonetic representations and hone in on which apps are potentially copying the originals. This thought was also made under the assumption that given a list of phonetically-similar apps, the app with the highest guild count was the most trustworthy.
