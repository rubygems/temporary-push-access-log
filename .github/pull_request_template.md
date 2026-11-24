<!--
Pull requests here add or update decision records. Only RubyGems.org operators should open them.
To request temporary push access, open an issue with the request form instead.
Undisclosed vulnerability? Do not open a pull request. Email security@rubygems.org.
-->

## Record

- Request issue: #
- Gem:
- Record file: `records/<gem-name>/<issue-number>.md`
- Type: <!-- Grant (new) | Grant update (activation, publication, correction, revocation) | Refusal or closure -->

## Checklist

- [ ] The record was copied from `templates/grant.md` or `templates/refusal.md`, and every field is filled in or marked "None".
- [ ] It contains no email addresses, private correspondence, identity documents, credentials, or undisclosed vulnerability details.
- [ ] People are named only by their public RubyGems.org or source-host account names.
- [ ] For a private security request, the advisory is public before this record is merged.

For a new grant:

- [ ] The contact attempt and response deadline for every relevant contact are recorded, and every deadline has passed, at least 14 days after its attempt unless a recorded emergency shortening applies.
- [ ] Two independent operators, neither the requester nor the grantee, have approved, with conflicts disclosed.
- [ ] The technical review of the changes and the final built gem files is recorded separately from the approvals.
- [ ] Every approved gem file is listed with its SHA-256 checksum.
- [ ] This record is merged before access is activated.

For a grant update:

- [ ] Activation and absolute expiry times are in UTC, with expiry 72 hours after activation.
- [ ] Publication outcome lists each accepted file, or records that it was not published.
- [ ] Any correction or revocation records its reason and approvals.
