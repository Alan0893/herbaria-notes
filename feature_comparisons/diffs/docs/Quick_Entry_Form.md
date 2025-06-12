
## Quick Entry Form

**Key Files and Structure:**

1.  **occurrencequickentry.php**:
    *   This is the central file for the quick entry interface. It serves as the main page where users interact with the form.
    *   It handles request parameters to determine the current collection (`collid`), image (`imgid`), occurrence record (`occid`), and navigation state.
    *   It initializes the `OccurrenceEditorManager` (or its specialized derivatives like `OccurrenceEditorDeterminations`) to interact with the backend.
    *   **Functionality**:
        *   Retrieves a list of image IDs (e.g., using `OccurrenceEditorManager::getImgIDs()`) and associated occurrence data.
        *   Displays a two-column layout:
            *   **Left Column**: Data entry fields for the occurrence record. The fields available are defined in `OccurrenceEditorManager` (e.g., `barcode`, `recordedby`, `eventdate`, `locality`, scientific name components, etc., as seen in the `$occArr` variable usage and the new fields in `OccurrenceEditorManager::$fieldArr`).
            *   **Right Column**: Displays the image associated with the current record, handled by quickentryimgprocessor.php.
        *   Provides navigation controls (e.g., "Previous", "Next", "Jump to page") allowing users to move through records/images quickly. The `navigateToRecordNew()` JavaScript function facilitates this.
        *   Handles form submissions for saving edits (`saveOccurEdits`) or adding new records (`addOccurRecord`).
        *   Manages user permissions (`$isEditor`) to control editing capabilities.
        *   Includes various JavaScript files for client-side logic, such as field change tracking (`fieldChanged()`), input validation, and dynamic UI updates (e.g., from collections.editor.main.js, collections.editor.query.js).

2.  **quickentryimgprocessor.php**:
    *   This script is included within occurrencequickentry.php to manage the image display.
    *   **Functionality**:
        *   Displays the specimen image.
        *   Provides image manipulation tools like zoom and rotation, likely using JavaScript functions from collections.editor.imgtools.js.
        *   May handle navigation between multiple images if several are linked to the same occurrence record context.

3.  **OccurrenceEditorManager.php**:
    *   This class is modified to support the quick entry workflow.
    *   **Modifications for Quick Entry**:
        *   The `$fieldArr` (or a similar structure defining occurrence fields) is expanded to include fields specifically useful for rapid data entry, such as `accesNum`, `filedUnder`, `currName`, `idQualifier`, `detText`, `provenance`, `container`, `collTrip`, `geoWithin`, `highGeo`, `frequency`, `prepMethod`, `format`, `verbLat`, `verbLong`, `method`.
        *   New public methods are added to fetch data required by the quick entry form:
            *   `getImgIDs()`: Retrieves a list of all image IDs, which the quick entry form can then iterate through.
            *   `getBarcode()`: Fetches the barcode associated with a given image ID.
            *   `getOneOccID()`: Retrieves the occurrence ID linked to a specific image ID.
            *   `getImageInfo()`: Gathers detailed information about an image.
        *   The `getDynamicPropertiesArr()` method is made public, potentially for use in the form.
        *   Existing methods like `editOccurrence()` and `addOccurrence()` are used to save the data entered through the quick entry form.

4.  **collprofiles.php**:
    *   This file, which displays collection profile information, is modified to include a link to the new quick entry form.
    *   This provides an access point for users to start a quick entry session for a specific collection, typically passing the `collid` and initial image/record parameters to occurrencequickentry.php.

**Overall Workflow:**

The user navigates from a collection's profile page (`collections/misc/collprofiles.php`) to the quick entry form (`collections/quickentry/occurrencequickentry.php`). The form displays an image (via `quickentryimgprocessor.php`) and corresponding data fields. The user transcribes data from the image into the fields. Upon saving or navigating, the data is processed by `OccurrenceEditorManager.php`, and the form updates to show the next image/record in sequence, facilitating a "rapid" data entry experience by minimizing clicks and page reloads for common transcription tasks.
