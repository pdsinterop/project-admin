Game plan voor milestones: 4b. Contacts and Profile and 4c. Calendar

Here is the text from the milestone:

4b. Contacts and Profile
Nextcloud users already have profile data like full name and avatar in their user account, and they also already have a Nextcloud addressbook in which they keep track of their contacts, for instance for sharing Nextcloud documents.

For this milestone we will unlock this data and make it available in the RDF-based Solid data format for profile and contacts data.

The details of both the Solid and the Nextcloud data format for this will be detailed on a dedicated public web page on https://pdsinterop.org/, with links to the relevant sections in the official Solid spec.

This milestone will implement Contacts and Profile in the Nextcloud app. This is an addition to the WebID profile from the "Identity Nextcloud Integration" milestone (1c).

4C. Calendar
Same as with Contacts and Profile but unlocking the user's Nextcloud-native calendar events as Solid-native calendar events.

Where certain fields don't have a mapping (e.g. if the Solid format has a maximum number of attendees for an event, but the Nextcloud format does not), they will simply be left blank. Other than that, it will be a great way to bootstrap the Solid app eco-system, where the millions of existing Nextcloud users can instantly use Solid apps with their existing data.

The details of both the Solid and the Nextcloud data format for this will be detailed on a dedicated public web page on https://pdsinterop.org/, with links to the relevant sections in the official Solid spec.

This milestone will implement Calendar in the Nextcloud app.

-----------
The plan for these milestones is to leverage FlySystem for contacts and calendar. The handling for profile will be a bit different.

Profile updates:
- implement PUT endpoint. Use easyRDF to read the parts from the turtle file that we know and store them in Nextcloud. Keep the rest as 'extra' fields.
- implement PATCH endpoint - start with the turtle representation, apply the patch, then reuse the code from PUT to apply the changes in Nextcloud;
- Up for consideration: should we wrap the profile in a flysystem-nextcloud-profile?

Wrap contacts in flysystem - each contact is a file, which by default will output as turtle. Conversion to JsonLD is already handled, so no need to worry about that.
This will allow us to reuse most of the code currently used in the /storage/ endpoint;
The difference will be that we have to wrap the internal nextcloud contacts API instead of the files API.

Steps we need to take for contacts:
- make a flysystem-nextcloud-contacts based on https://github.com/pdsinterop/flysystem-nextcloud that uses the contacts API instead of the files API. The aim is to create a single "directory" with contacts in it as files.
- create the endpoints for /contacts/ (copy from /storage/);
- create the contacts controller (copy from storage controller, use php-solid-crud but with flysystem-nextcloud-contacts as the backend - should not need huge modifications for this)

For calendar the steps are very similar to contacts:
- make a flysystem-nextcloud-calendar, use the calendar/events api instead of files. On the fence about the structure - each day on the calendar can be a directory with events in them as files; And have events be listed in the root of the directory.
- create endpoints for /calendar/
- create the calendar controller (copy from storage controller, use php-solid-crud but with flysystem-nextcloud-calendar as the backend - should not need huge modifications for this)

All three have their own endpoints:
- https://nextcloud.local/apps/solid/@alice/profile/turtle
- https://nextcloud.local/apps/solid/@alice/contacts/
- https://nextcloud.local/apps/solid/@alice/calendar/

-------

The profile endpoint will implement:
GET /profile/turtle
Fetch the profile information as turtle (already implemented)

PUT /profile/turtle
Puts a new turtle profile. Relevant information should be stored in nextcloud - whatever we don't understand, just store as 'extra' fields.

PATCH /profile/turtle
Update a field in the turtle profile using SparQL - we can optionally skip this;

-------
The contacts endpoint will implement:
GET /contacts/
Fetch the contacts for the user and output the information as turtle directory listing.

GET /contacts/:id/
Fetch a specific contact - the ID will be the internal nextcloud ID for this contact if such a thing exists;

POST /contacts/
Create a new contact in the addressbook of the user. Return the newly created ID;

PUT /contacts/:id/
Update an existing contact. Unhandled fields are discarded? If we have the option to store extra fields, do that;

DELETE /contacts/:id/
Delete an existing contact

PATCH /contacts/:id/
Update a field for an existing contact using SparQL

-------
The calendar endpoint will implement:
GET /calendar/
Fetch the calendar for the user and output the information as turtle directory listing.

GET /calendar/:id/
Fetch a specific event - the ID will be the internal nextcloud ID for this event if such a thing exists;

GET /calendar/:day/
Fetch the calendar events for a specific day, output as a turtle directory listing;

POST /calendar/
Create a new event in the calendar of the user. Return the newly created ID;

PUT /calendar/:id/
Update an existing event. Unhandled fields are discarded? If we have the option to store extra fields, do that;

DELETE /calendar/:id/
Delete an existing event

PATCH /calendar/:id/
Update specific fields in an existing event
