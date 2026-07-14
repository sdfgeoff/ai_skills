---
name: break-work-into-tickets
description: Take a chunk of work that will require lots of code changes and split it into managable tasks. Use this any time a change will likely influence more than a few files.
---

Create a plan with the user as to the major chunks of work. At every stage in the plan. Build things as you need them (there should be no dead code). Eg: refactor as one ticket, implement the feature in the next. If you need to split a file or package into two, make a ticket for it. Think about when/where/how you will test your changes.

Present these to the user as a bullet point list with a short summary. When the user approves it, make a folder called `todo` and another folder called `done`. Inside these you will create detailed tickets as markdown files (eg `todo/001-refactor-file.md`). Ask the user to review them. If you have discussed data models or other specifics, make sure these are present in the ticket.

When the user has approved the tickets, take a ticket from `todo` and implement it. Commit your changes after the ticket. Then move the ticket into `done`.

Do not commit the `todo` or `done` folder.
