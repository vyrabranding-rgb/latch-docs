# Changelog

## 1.0.0 — unreleased

Initial release.

- Check out / check in attachments from the page header, page actions or the lock table, on pages and blog posts.
- "Notify me when free" with @mention comments.
- Overwrite warnings when someone uploads a new version of a checked-out file.
- Force check-in for configurable admin groups.
- Optional automatic expiry, optional required note, configurable note length.
- Locked files (Latch) macro.
- Hourly housekeeping for expired locks.
- Licence enforcement: when Forge reports an inactive licence, locks stay visible but check-out, check-in and notifications are paused with a clear banner.

### Review pass (2026-09-18)

A five-lens adversarial review found 17 issues, all fixed before first deployment:

- Settings resolvers were reachable from page modules; they now live on a separate Forge function bound only to the administration module, with a module check as defence in depth.
- Permission checks ran as the app, which Confluence only allows for administrators; they now run as the user, for the user.
- Blog posts were not supported (page-only attachment route); pages and blog posts are both handled, and comments target the right container.
- Storage collections were arrays under one key (lost updates under concurrency); every collection is now one key per member, lock + index marker are removed in one transaction, and upload events are deduplicated with atomic claim markers.
- Expired-but-unswept locks had different meanings in different places; liveness is now defined once.
- Check-in and "notify me" could be used to probe whether files on other pages were locked; lookups are scoped to the current page first and failures share one message.
- A zero note limit could make check-out impossible; the floor is now 1.
- Page rendering read one storage key per attachment; it now reads only the locked ones, in batches. The byline no longer writes on read.
- An attachment moved to another page or blog post keeps its lock (re-homed on the next event).
- Duplicated helpers and table cells were consolidated; the Confluence client gained tests for pagination, permission-denied and not-found paths.
