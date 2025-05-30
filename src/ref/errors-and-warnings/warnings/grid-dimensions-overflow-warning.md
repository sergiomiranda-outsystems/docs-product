---
summary: Learn how to resolve grid dimensions overflow in OutSystems 11 (O11) by adjusting widget properties to fit within defined grid boundaries.
locale: en-us
guid: 8faa36bf-6acf-423b-9fc7-9e365c55697e
app_type: traditional web apps, mobile apps, reactive web apps
platform-version: o11
figma:
tags: ui design, user experience, responsive design, grid system, technical troubleshooting
audience:
  - frontend developers
  - full stack developers
  - ui designers
outsystems-tools:
  - service studio
coverage-type:
  - unblock
---

# Grid Dimensions Overflow Warning

Message
:   `The sum of the 'Width' and 'Margin Left' properties of the widget must be set within the grid boundaries`

Cause
:   The widget has its Width and Margin Left properties set using 'col' and the sum of the two is exceeding the number of columns defined in the theme's grid.

Recommendation
:   Change Width or Margin Left properties of the element so that they fit within the grid, or change the Grid property of the Theme to increase the number of columns of the grid.
