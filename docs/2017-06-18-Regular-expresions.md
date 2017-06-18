---
layout: post
title:  "Regular Expresions in JS"
date:   2017-06-18 12:53:01 +0300
categories: Regular Expresions
---

## I was asked to give a short intro to regexp in js
The utility I created for handling I18N uses regexp in it's configuration.

So what is regexp?
how can we use it?
and more..

## What is regexp?
__Regexp__ - is short for regular rexpresion.  
Regular expresion is a way to formalize a string into a pattern.  
regular expresion are used in many programing environment
* Java
* JavaScript
* PHP
* bash scripts
* etc ...

The idea is that you use a pattern to find or manipulate a String or sub-string.  
Note that regular expresions are not the same in all lenguages, but the logic is the same.

## how can we use it?
Regep are usaly used in find/replace/verify use cases.
in JS tou can use 2 variant of regular expresion:
* a String (str.match(regexp);)
* a RegExp object (regexObj.exec(str))

The RegExp object is used when the same sub patterns return multiple valuse, each needs to be handled on its own.

## Patterns
I'm not going to list the patterns here, I added links to them in the Usefull links section.

## Flags (in JS)
* __g__ - Global search.
* __i__ - 	Case-insensitive search.
* __m__ - 	Multi-line search.
* __u__ - 	unicode; treat pattern as a sequence of unicode code points
* __y__ - 	Perform a "sticky" search that matches starting at the current position in the target string.
[Stiky explanation in MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/sticky)

## Break down a complicated example
the regex:  
```
/<Action(?(?=[^\<\>]*\Wlabel)(?:[^\<\>]*\Wlabel)|(?:[^\<\>]*\Wname))\W?=\W?((['"])[^'"]*\2)/gm
```
> **/** - start of regexp  
> **<Action** - matches the string '<Action'  
> **(?** - a pattern for if then else  
> **(?=** - look ahead pattern  
> **[^\<\>]*** - any character that is not < nor > 0 or more times  
>  **\W** - white space  
>  **label** - matches the string 'label'  
>  **)** - end of the look ahead pattern  
>  **(?:** - match without remembering the match  
>  **[^\<\>]*** - any character that is not < nor > 0 or more times  
>  **\W** - white space  
>  **label** - matches the string 'label'  
>  **)** - end of match without remembering pattern  
>  **|** - seperates the then from the else  
>  **(?:** - match without remembering the match  
>  **[^\<\>]*** - any character that is not < nor > 0 or more times  
>  **\W** - white space  
>  **name** - matches the string 'name'  
>  **)** - close the match without remembering  
>  **)** - close the if then else pattern  
>  **\W?=\W?** - the char '=' with or without white spaces adjacent  
>  **(** - start of group 1  
>  **(['"])** - group 2 is one of ' or "  
>  **[^'"]*** - any sequance of characters that don't include the chars ' or "  
>  **\2** - a String identical to the match of group 2  
>  **)** - end of group 1  
>  **/** - end of regexp
> ***
> **gm** - the flags global and multiline

In short this regexp finds all action tags, and extracts from them the label, if there is no label it takes the name.

## Usefull Links
* [Patterns in java](https://docs.oracle.com/javase/7/docs/api/java/util/regex/Pattern.html)
* [Patterns in JS (by mozilla)](https://developer.mozilla.org/en/docs/Web/JavaScript/Guide/Regular_Expressions)
* [RegExp in JS](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec)