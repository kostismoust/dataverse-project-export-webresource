# Dataverse Project Export Web Resource

A dependency-free Dynamics 365 Project Operations HTML web resource that exports Project Tasks and Time Entries to a formatted `.xlsx` workbook.

## Features

- Uses the model-driven app `Xrm.WebApi` context.
- Supports Dataverse paging.
- Sorts tasks by WBS and time entries by date/resource.
- Writes OOXML directly in the browser; no CDN or external JavaScript dependency.
- Produces numeric Excel cells for hours and progress.

## Files

- `src/project-export-dialog.html` — upload as an HTML web resource.

## Expected input

Open the web resource with URL-encoded JSON in the `data` query parameter:

```json
{
  "projectId": "00000000-0000-0000-0000-000000000000",
  "projectName": "Example project"
}
```

As a fallback, the same JSON can be placed in browser local storage under `d365_project_export_context`.

## Deployment

1. Add the HTML file as a web resource in an unmanaged solution.
2. Add a command-bar button or form action that opens the web resource and passes `projectId` and `projectName`.
3. Publish customizations.
4. Test with users who have read access to Project Tasks and Time Entries.
5. Confirm exported descriptions do not contain personal or customer-confidential data before sharing the workbook.

## Compatibility note

The sample uses standard Project Operations logical names such as `msdyn_projecttask`, `msdyn_timeentry`, and `_msdyn_project_value`. Verify them in your environment and update the column definitions in the HTML if required.

## License

No license is included. Add one only after confirming that you or your employer own the code and approve publication.
