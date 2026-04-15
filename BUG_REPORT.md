Bug Report
1. Pagination Offset Logic
Discovery: Found during unit testing of taskService.getPaginated.

Issue: The offset was calculated as page * limit, causing Page 1 to skip the first set of results.

Fix: Updated calculation to (page - 1) * limit.

2. Task Completion Side-Effect
Discovery: Found during integration testing of PATCH /tasks/:id/complete.

Issue: Completing a task automatically reset the task priority to "medium," losing the user's original data.

Fix: Removed the hard-coded priority field from the completion update logic.

3. Loose Status Filtering
Discovery: Found while testing GET /tasks?status=....

Issue: The code used .includes() for status filtering, allowing partial matches (e.g., searching "todo" returned "todo-later").

Fix: Changed to strict equality === for precise filtering.
