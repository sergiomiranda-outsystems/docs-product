---
summary: OutSystems 11 (O11) issues an 'Invalid External Site' error when a URL in an External Site element is incorrectly wrapped in quotes.
locale: en-us
guid: 8e1138a1-e294-4b9a-a0f6-79ff3f8b9865
app_type: traditional web apps, mobile apps, reactive web apps
platform-version: o11
figma:
tags: error handling, external integrations, debugging, best practices
audience:
  - mobile developers
  - frontend developers
  - full stack developers
outsystems-tools:
  - service studio
coverage-type:
  - unblock
---

# Invalid External Site Error

The `Invalid External Site` error is issued in the following situation:

* `'URL' value must not have wrapping quotes`
  
    You have an External Site in your module with "" or ". They are not allowed because it might lead you to a wrong site.
    
    Edit the External Site element and fix the value set in the URL property.
