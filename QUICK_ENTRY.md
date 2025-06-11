## Quick Entry Form Feature

### Core Data Entry Interface & Logic:
- `occurdataentry.php` : script seems to be the heart of the quick-entry feature.
  - Renders the HTML form with various input fields for occurrence data (e.g., collector, date, locality, scientific name).
  - Handling the submission of new records (`$action == 'Add Record'`).
  - Integrating with backend classes like `OccurenceEditorManager` to save the data.
  - Including the necessary Javascript files for client-side interactions and enhancements. The path `dev/` seems to suggest that this might be a newer version of the data entry form for rapid input???
- `OccurenceEditorManager.php` : class manages the business logic for creating and editing occurrence records. 
  - Receive data submitted from the `occurdataentry.php` form.
  - Validate and process the input.
  - Interact with the database to save new occurrence records. 
  - It contains a list of field mappings, some of which are explicitly noted for a "quick entry form" (e.g. `accesNum`, `filedUnder`, `currName`)

### Client-Side (JavaScript):
- `collections.editor.main.js` : enhances the data entry form by:
  - initializing numerous autocomplete widgets for various fields (e.g., `ffsciname` for scientific names, `exstitleinput` for exsiccati titles, `ffrecordedby` for collectors, `ffcountry`, `ffstate`, `ffcounty` for localities, and `associatedtaxa`). Autocompletion significantly speeds up data input by suggesting values as the user types.
  - Handling form events and potentially dynamic updates to the form. 
- `collections.editor.autocomplete.js` : specifically focuses on setting up autocomplete functionality for geographic fields like `country`, `stateprovince`, and `county`, making locality data entry faster.
- `autocomplete-input.js` : defines a custom HTML element (`<autocomplete-input>`) that provides a reusable and enhanced autocomplete input field. Likely used throughout the quick-entry form to power the suggestion and selection of values for different fields, contributing to the "rapid" aspect of the data entry. Handles fetching suggestions, displaying them, and managing user interaction with the autocomplete menu.
- `collections.editor.query.js` : primarily for querying. Functions like `navigateToURL` (e.g., to a transcription page) or `toggleDetail` (to switch between minimal and detailed views) could be leveraged within a quick-entry workflow to streamline navigation. 

### Styling:
- `quickentry.css` : provides the specific styles for the quick-entry form. 

### Other Files:
- `occurrenceeditor.php` - the quick-entry form might be a streamlined version of this or share some backend logic. `QUICK_HOST_ENTRY_IS_ACTIVE` suggests that some quick entry features might be integrated here as well???
- Various RPC scripts in `rpc` (`e.g., `getspeciessuggest.php`, `getGeography.php`) are used by the autocomplete functions to fetch suggestion data from the server.  
