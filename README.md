# volto-fullcalendar-block

forked from [mbarde/volto-fullcalendar-block](https://github.com/mbarde/volto-fullcalendar-block)

Block for [Volto](https://github.com/plone/volto) to display events from an iCal/ics file in a [FullCalendar](https://fullcalendar.io/).

## Features


### Listing block variation for Plone events

https://user-images.githubusercontent.com/4497578/154287664-6153ae22-27dd-48ed-984a-93817ef70431.mp4

* Display events within a listing block as calendar
* In order to display recurrent events, you need to add a catalog index and metadata column:

```XML
<?xml version="1.0"?>
<object name="portal_catalog">
    <index name="recurrence" meta_type="FieldIndex">
        <indexed_attr value="recurrence"/>
    </index>
    <column value="recurrence"/>
</object>
```
More details checkout the following link: https://5.docs.plone.org/external/plone.app.dexterity/docs/advanced/catalog-indexing-strategies.html#adding-new-indexes-and-metadata-columns


### Calendar block for remote events

https://user-images.githubusercontent.com/4497578/154287676-295386f9-faac-47e8-b0ef-f017f8c80dde.mp4

* Specifiy an URL to an .ics/.iCal file -> Contained events are displayed in the calendar using FullCalendars [iCalendar plugin](https://fullcalendar.io/docs/icalendar)

### Configure FullCalendar toolbar via block settings

https://user-images.githubusercontent.com/4497578/154287799-eca71fe0-4ce2-4e9d-8921-9729e191f2fc.mp4

### Note

This fork adds some additional options to the sidebar to configure the calendar, so far :
"Show Weekends" and "Time Format 24"

## Setup

### Add volto-fullcalendar-block to your Volto project

## !!! No registration of this addon in yarnpkg yet !!!

1. Make sure you have a [Plone backend](https://plone.org/download) up-and-running at http://localhost:8080/Plone

   For example [Docker container](https://6.docs.plone.org/install/containers/) via command:

   ```
   docker run --name plone -p 8080:8080 -e SITE=Plone -e PROFILES="profile-plone.restapi:blocks" plone
   ```

2. Start Volto frontend

- If you already have a volto project, just update `package.json`:

  ```JSON
  "addons": [
      "@filith/volto-fullcalendar-block"
  ],

  "dependencies": {
      "@filith/volto-fullcalendar-block": "*"
  }
  ```

- If not, create one:

  ```
  npm install -g yo @plone/generator-volto
  yo @plone/volto my-volto-project --addon @filith/volto-fullcalendar-block
  cd my-volto-project
  ```

3. Install new add-ons and restart Volto:

   ```
   yarn
   yarn start
   ```

4. Go to http://localhost:3000

## Tests

Expects Volto to run on `http://localhost:3000` by default (see `cypress.json`).

Run tests: `yarn cypres:run`
