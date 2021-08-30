---
templateKey: blog-post
title: "Python: How many days, minutes and seconds does the year have?"
date: 2021-08-30T17:43:39.843Z
description: A simple introduction to Python
featuredpost: true
featuredimage: /img/python_logo_and_wordmark.svg.png
tags:
  - python
  - math
  - ""
---
For New Years we are writing a Python program that calculates days, hours and seconds of a given year. It also checks if the year is a leap year and adds a day.

The result looks like this

[![](http://yearofpython.com/wp-content/uploads/2017/12/Bildschirmfoto-2017-12-30-um-15.31.02-1-300x94.png)](http://yearofpython.com/wp-content/uploads/2017/12/Bildschirmfoto-2017-12-30-um-15.31.02-1.png)

This is the code:

```python
def day_hours(year, is_leap_year):
    if (is_leap_year):
        days = 366
    else:
        days = 365
    print ("The year " + str(year) + " has:")
    print ("Days: " + str(days))
    print ("Hours: " + str(int(days)*24))
    print ("Minutes: " + str((int(days)*24)*60))
    print ("Seconds: " + str(((int(days)*24)*60)*60))


day_hours(2018, False)
```