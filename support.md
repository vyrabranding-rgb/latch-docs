# Latch — Documentation and Support

## Getting started (30 seconds)

1. Open any Confluence page or blog post that has attachments.
2. In the page header, click **Attachment locks** (or use the page's
   **… → Manage attachment locks**).
3. Next to the file you are about to edit, click **Check out** and,
   optionally, say why.
4. Edit the file, upload the new version, then click **Check in**.

Everyone who opens the page now sees "1 locked file" in the header and your
name next to the file.

## What colleagues see

- **Checked out** files show who has them, since when, and the note.
- **Notify me when free** sends you an @mention comment the moment the file
  is checked in or its lock expires.
- If someone uploads a new version of a checked-out file anyway, Latch posts
  a page comment mentioning both people, and the lock table lists the
  warning under **Show recent overwrite warnings**.
- Metadata-only edits to a file (renaming, comments) are not treated as
  overwrites.

## Administrators

**Confluence administration → Latch attachment locks** has four settings:

| Setting | Meaning | Default |
|---|---|---|
| Groups allowed to force check-in | Members can check in anyone's file (the **Force check-in** button) | confluence-admins, site-admins, administrators |
| Automatically release check-outs after N hours | 0 = never; otherwise an hourly job releases stale locks and tells watchers | 0 |
| Maximum note length | Characters allowed in the check-out note (1–500) | 200 |
| Require a note | Users must say why they are checking a file out | off |
| Post a comment on overwrite / on availability | Toggle each kind of @mention comment | on / on |

## Permissions

- Anyone who can view the page sees the lock table.
- Checking out and "Notify me" require **edit** permission on the page.
- Checking in is for the person who holds the lock, or members of the
  force-check-in groups.

## The "Locked files (Latch)" macro

Insert it into a page body (type `/Locked files`) to show a read-only list
of that page's checked-out files.

## Frequently asked questions

**Can Latch block an upload?** No. Confluence Cloud offers no API to prevent
uploads, so no cloud app can. Latch makes locks impossible to miss and turns
an overwrite into an immediate, attributed warning.

**Where is the data stored?** In Atlassian Forge storage for your site.
Nothing leaves Atlassian. See the [Privacy Policy](privacy-policy).

**What happens when the trial ends?** Existing locks stay visible; checking
out and in is paused until an administrator subscribes.

**Does it work on blog posts?** Yes, identically.

## Support

Email **vyra.branding@gmail.com**. Target first response: two business days.
Please include your site URL, the page URL and what you expected to happen.

## Release notes

See [CHANGELOG](https://github.com/vyrabranding-rgb/latch-docs/blob/main/changelog.md).
