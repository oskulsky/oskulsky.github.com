---
title: Create-me A simple utility to auto generate actions and views
---

[![New ProImage](/images/ProImage.png)](http://www.new-proimage.com/)
# Create-me  
__Developer:__ Ofer Skulsky (@oskulsky)  
__Company:__ new-proimage (@new-proimage)  
__License:__ Private

## What is it
The Create-me utility is a small utility to help stream line and expodite development.  
It adds what needs to be added to configuration XMLs and generates code stubs for server and client.

## Who does it work
The utility is written in `node.js`.  
The nice utility feel, is from using `commander.js`,  
The interactive input, is from using `inquirer`,  
The code generation uses `fs.s`, `mkdirp.js` and `path.js`.  
Running npm link from the root folder of `Create-me` enables it from every folder.  
The I dea behind the utility was:
* Keep stubs for all the "parts" that can be created in the system.
* Ask developer friendly questions he can anderstand
* Automaticly "fix" configurations and XML files, create basic files