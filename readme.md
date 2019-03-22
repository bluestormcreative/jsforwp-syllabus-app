# Syllabus Calendar Plugin App Thingy
### To be broken down into v1 / v2 and beyond...
This might be a React app on the frontend as well as Gutenberg blocks on the back end. Either of those parts could comprise v1 or v2, etc.

**Pain point: The most important part of this is the date range functionality. Setting up the dates correctly on a syllabus is the problem we want to solve with the Magic of Computers.**

## Ideas on where to start for v0.0.1
1) Build a form with JS with 3 fields: (maybe react???)
    - start date: datepicker
    - end date: datepicker
    - class days: select
2) On submit, date range is filtered to only include those dates
    - libraries to help: moment.js / moment-range
3) Page shows a preview of the filtered date range (all dates listed out)
4) Optional: it would be cool if the dates could be grouped by week at this point
5) Optional: clicking on a date in the range removes it from the final range
6) Optional: extra datepicker field when range is showing to add additional dates

## Random thoughts
1) What if this whole thing was a wizard?
    - Once the date range is set, it walks you through each date to set up the class activity / to-do data
2) Optional: super awesomeness would ensue from being able to export this to Google / iCal

## Example of syllabus table layout
This is what we're trying to improve upon...
![Example syllabus table layout](https://raw.githubusercontent.com/bluestormcreative/jsforwp-syllabus-app/master/example-syllabus-table.png)


### Possible Backend / admin for "Gutenberg version"
1) Create custom post type "syllabus"
2) Create custom taxonomy of "semester"
    - attach to syllabus cpt
    - non-hierarchical
3) Expose both cpt and tax to REST api
4) Syllabus gutenberg setup (maybe post template?)
    - title: name of course
    - 3 blocks, 2 custom
        1. course info (simple table / grid)
        2. rich text (default) - will be used twice in template for boilerplate info
        3. syllabus table (very complicated table /grid)
5) course info block
    - fields
        - Term: semester taxonomy
        - Department: text
        - Location: text
        - Days and Times: text or datepicker?
        - Start date: datepicker
        - End date: datepicker
        - Instructor: text
        - Email: text
        - Office Location: text
        - Address: text / address? google map?
        - Office Hours: text
    - display in block in two columns if possible
6) syllabus block
    - might be too much for a single block
    - table columns
        - day
        - date
        - class activity
        - to do / due dates
    - table rows divided by weeks (as _th_ tags that span all columns)
7) **the dream is to put in the start date, end date, and days of the week that class meets and have all the dates in this table populate automagically from there.**
    - datepicker for start and end dates
    - select field (select2) for days of the week
    - use this data to filter out the date range and grab all dates
    - moment-range library can help
    - maybe a way to exclude a date? in case of holidays etc.
8) can block fields be pre-populated? maybe by an options page?
    - if this is true, then give the option to override field content per post
    - this would also be good for boilerplate text
9) Expose all these fields to REST api
10) Syllabus posts should be clone-able

### Frontend
1) Make pretty.
2) Make easy to view on mobile.
