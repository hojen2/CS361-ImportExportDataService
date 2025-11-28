# COMMUNICATION CONTRACT
### ---Requesting Data---

- file: import_export_requests.json
- format: JSON array of request objects

[ { "operation": "EXPORT", "data": { "source_file_path": "file.json", "file_path": "backup.json" } }, { "operation": "IMPORT", "data": { "file_path": "backup.json" } } ]

Operations and Data

- EXPORT – copy data from a source file to a backup file.
- source_file_path (required): path to the file to export.
- file_path (required): path where the backup should be saved.
- IMPORT – load data from a backup file.
- file_path (required): path to the backup file to import.

- Example Request Call:



[ { "operation": "EXPORT", "data": { "source_file_path": "habits.json", "file_path": "habits_backup.json" } } ]

[ { "operation": "IMPORT", "data": { "file_path": "habits_backup.json" } } ]

### ---Receiving Data---

- file: import_export_responses.json
- format: JSON array of response objects
- Responses generally include a status and message. For IMPORT requests, imported_data contains the loaded data.

- Example Response Call:



EXPORT success:
[ { "status": "success", "message": "Export successful. Copied habits.json to habits_backup.json." } ]

IMPORT success:
[ { "status": "success", "message": "Import successful: habits_backup.json", "imported_data": [ { "name": "Jogging", "period": "week", "frequency": 5, "category": "fitness" } ] } ]

Error example:
[ { "status": "error", "message": "Export failed: File not found" } ]
