# Latch — Security Policy

_Last updated: 23 September 2026_

Published by **VYRA**, Stockholm, Sweden.

## Architecture

Latch is an Atlassian Forge app. It has no servers, no database and no
infrastructure of its own. All code runs on Atlassian's Forge platform inside
Atlassian's cloud, and all data is stored in Forge hosted key-value storage
belonging to the customer's own Atlassian site.

The app declares **no external egress**: it cannot send data to any address
outside Atlassian, and Forge enforces this at the platform level. There is no
remote API, no webhook endpoint and no third-party service.

## Data protection

- **In transit:** all traffic is between Atlassian services over TLS, managed
  by Atlassian.
- **At rest:** Forge hosted storage is encrypted at rest by Atlassian.
- **Data residency:** because Latch stores data only in persistent Forge
  hosted storage, it inherits the customer site's data residency pinning
  automatically.
- **Retention:** lock records live until check-in, expiry or deletion of the
  file. Overwrite warnings expire automatically after 90 days. Uninstalling
  the app removes the app's storage.

## Access control

- The page or blog post is always taken from the Forge context, never from
  the client, so a user cannot act on content they are not viewing.
- Attachments are listed and read **as the requesting user**, so files the
  user cannot see never appear.
- Checking a file out, and asking to be notified about one, require **edit**
  permission on the content, verified with Confluence's own permission API.
- Checking a file in is limited to the lock owner or members of the
  administrator-configured groups.
- Administration settings are served by a separate Forge function that only
  the Confluence administration module can invoke.
- No member of VYRA can access customer data. We have no console, no
  database and no log pipeline containing customer content.

## Least privilege

Latch requests the minimum scopes required for its function. Each scope and
its justification is listed on the app's Privacy and Security tab in the
Atlassian Marketplace.

## Secure development

- TypeScript in strict mode, ESLint, and an automated test suite that must
  pass before any release.
- Dependencies are limited to the official `@forge/*` packages and React.
- Every release is reviewed before deployment, including an adversarial
  review pass covering authorisation, injection, concurrency and data
  exposure.
- Source code is held in a private repository with two-factor authentication
  enabled on the account.

## Vulnerability reporting

Report suspected vulnerabilities to **security@** our domain (see the contact
address on the app's Marketplace listing). Please include reproduction steps
and the affected site.

Our commitments:

| Stage | Target |
|---|---|
| Acknowledgement | 2 business days |
| Initial assessment and severity | 5 business days |
| Fix for critical issues | in line with Atlassian's Marketplace Security Bug Fix Policy |

We follow Atlassian's Marketplace Security Bug Fix Policy for severity levels
and remediation deadlines, and will notify affected customers and Atlassian
as required by the Marketplace Partner Agreement.

## Incident response

If we become aware of a security incident affecting the app, we will
investigate immediately, notify Atlassian through the Ecosystem support
portal, and inform affected customers by email at the contact address on
their subscription, without undue delay and within the timeframes required
by applicable law.
