FogBugz Importer reads tickets (cases) data from an Excel spreadsheet and automatically imports that data into FogBugz using FogBugz XML API.

You can prepare a spreadsheet with data by hand or with some tool. If you migrating from Unfuddle then you may want to check [Unfuddle Backup Parser](http://code.google.com/p/unfuddle-backup-parser/). That parser will process your backup file and prepare spreadsheet for you.

Usage:<br>
<code>FogBugzImporter.exe FogBugzApiUrl "Your Name" "Your Password" "X:\Path\To\tickets.xlsx"</code>

Example:<br>
<code>FogBugzImporter.exe https://your-account.fogbugz.com/api.asp "John Doe" "Strong password" "C:\Users\John Doe\Documents\tickets.xlsx"</code>

<b>NOTE:</b><br>
<ul><li>You should create users, projects, areas, milestones in FogBugz before import.<br>
</li><li>You may want to tune up workflow in FogBugz before import if you need non-standard workflow.<br>
</li><li>There should be folder media next to tickets.xlsx even if you don't plan to import attachments to tickets.</li></ul>

The format of the tickets.xlsx is as follows (you may download sample tickets.xlsx using link on the right of this page or in <b>Downloads</b> section):<br>
<ul><li>number of rows is unrestricted.<br>
</li><li>first row is reserved (used as header) - data in it won't be imported.<br>
</li><li>data from first 12 columns (A to L, inclusive) will be processed.<br>
</li><li>column A (cmd) contains one of the FogBugz commands (new, edit, assign, reactivate, reopen, resolve or close). An empty cell in this column will cause stop of processing.<br>
</li><li>column K contains reporter (author) name. This column should not contain empty cells.<br>
</li><li>each other cell (B, C, D, E, F, G, H, I, J and L) can be empty.<br>
</li><li>DateTime values in columns B (dt) and J (dtDue) should be in UTC format.<br>
</li><li>values in columns C (sProject), D (sArea) and E (sFixFor) should correspond to existing (created in FogBugz) project, area and milestone names.<br>
</li><li>values in columns I (sPersonAssignedTo) and K (reporter) should correspond to existing (created in FogBugz) user names.<br>
</li><li>attached files are presented as string with format <code>attachment-name;attachment-file-name</code>. attachment-file-name should point to a file in <code>media</code> folder next to tickets.xlsx.</li></ul>

Here is a screenshot of sample tickets.xlsx<br>
<a href='http://habreffect.ru/files/45e/7cfc5d87d/tickets_shot-highlighted.png'><img src='http://habreffect.ru/files/93e/4394d9e4b/tickets_shot-highlighted-preview.png' /></a>