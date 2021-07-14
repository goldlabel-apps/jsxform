
## JSXForm

### What is JSXForm?

It's the part of our app which deals with managing user data so it needs to be bomb proof. To be honest I fell into the usual developer trap of underestimating the complexity of a task. You'd think you'd learn not to do that after 20 years, but you don't.

So as the development of JSXForm has iterated over the past month I've got a clearer list of what such a module needs to do. It needs to address the following agile stories;

- Render a form that can be described by an easy to read and edit file by a non-developer
- Understand and translate between the various data shapes in the API
- Can be used for both editing and creating new records
- Use a set of Input Components (Based on Material UI) which correspond to the types of information each field requires, (eg: InputString) 
- Reminders Input Component (Multiple Time based events) 
- Attachments Input Component (Uploading Images) 
- Validate that minimum form requirements are met (required fields) 
- Submit correctly formatted resource JSON object to the API 
- Deal with effects in React frontend (Modal Loading Overlay) 

Everyone hates forms, so let's make them easy. Using Material UI React components we can load a form as a JSON file, render it, validate it and send the information where it needs to go maybe as a WordPress plugin.

```javascript
export const allergyForm = {
    title: `Allergy Form`,
    reduxKey: `Allergy`,
    description: `Manage your allergies`,
    route: `/personal-health/allergy/`,
    icon: `allergy`,
    fields: [
        {
            label: `Allergen`,
            id: `allergen`,
            mapKey: `allergen`,
            type: `InputString`,
            helperText: `What caused the reaction?`,
            autoFocus: true,
            required: true,
        },
        {
            label: `Reactions`,
            id: `reactions`,
            mapKey: `reactions`,
            type: `InputStringArray`,
            helperText: `eg. Swelling`,
            multiline: true,
            required: true,
        },
        {
            label: `Severity`,
            id: `severity`,
            mapKey: `severity`,
            type: `InputRadio`,            
            options: [
                {
                    label: `Mild`,
                    value: `3`,
                },
                {
                    label: `Moderate`,
                    value: `5`,
                    defaultSelected: true,
                },
                {
                    label: `Severe`,
                    value: `7`,
                },
            ],
        },
        {
            label: `Date Identified`,
            id: `dateIdentified`,
            mapKey: `dateIdentified`,
            type: `InputDatetime`,
            helperText: `DD/MM/YYYY`,
        },
        {
            label: `Attachments`,
            id: `attachmentUrls`,
            mapKey: `attachmentUrls`,
            type: `InputAttachment`,
            helperText: `Attach Document?`
        },
    ]
}

```

by [listingslab](https://listingslab.com)

```bash

   ___    __  _               __     __
  / (_)__/ /_(_)__  ___ ____ / /__ _/ /
 / / (_-< __/ / _ \/ _ `(_-</ / _ `/ _ \
/_/_/___|__/_/_//_/\_, /___/_/\_,_/_.__/
                  /___/

```
