# RubyGems.org Temporary Push Access Log

This repository is the public log of requests made under the RubyGems.org Temporary Push Access Policy, and of every decision RubyGems.org operators make on them.

## What the policy is for

In rare cases, RubyGems.org lets a maintainer publish **one release** of a gem they do not own.
That happens only when all of these are true:

- the Ruby ecosystem depends on the gem and leaving it without releases would harm its users;
- people other than the owner hold merge rights on the gem's canonical repository and are using them;
- those maintainers have a release ready, accepted through the project's normal process;
- the existing owners, authorized publishers, and relevant organization administrators cannot be reached to publish it.

A grant is an operator-issued API key that can publish the approved files for one version, for at most 72 hours.
It does not make anyone an owner or maintainer of the gem, and it cannot yank, manage owners, transfer the gem, or change publishing settings.

The policy is **not** a route around an owner who replies and declines, a substitute for account recovery, or a way to settle disputes between owners.
If nobody but the owner holds merge rights, fork the gem under a new name instead.

## Undisclosed vulnerabilities: do not open an issue

If the release fixes a vulnerability that is not yet public, **email security@rubygems.org** and do not open an issue, pull request, or public notice anywhere.
We handle those requests privately and publish their record here once the advisory is out.

See [RubyGems.org security](https://rubygems.org/pages/security) for how we handle security reports.

## Keep private information out of this repository

Everything here is public and permanent.
Do not post:

- email addresses, phone numbers, postal addresses, or other personal contact details, including the owners' or your own;
- identity documents or anything else used to identify the grantee to Ruby Central;
- private correspondence with gem owners, or quotes from it;
- undisclosed vulnerability details, exploit code, or private security patches;
- API keys, OTP codes, or any other credential.

Refer to people by their public RubyGems.org and source-host account names only.
Operators will contact you privately for anything else they need.

## How to request temporary push access

1. Confirm the request fits the policy, and that the vulnerability, if any, is already public.
2. Open an issue with the **[Temporary push access request](https://github.com/rubygems/temporary-push-access-log/issues/new?template=request.yml)** form and fill in every required field.
3. Operators reply on the issue, ask for anything missing, and start contacting the existing owners.

### What you need to provide

| You provide | Why |
| --- | --- |
| The gem name and its canonical repository, with evidence that the repository is canonical (the gem's metadata, or the repository its last owner-published version was built from) | An unrelated fork does not qualify. |
| Why the ecosystem depends on the gem (for example, how many gems and applications use it, and how hard it would be to move off it) | Operators judge importance case by case. |
| Links showing that people other than the owner hold merge rights and are using them | The policy only applies to gems that are still maintained. |
| What you know about the existing owners and publishers being unavailable, using public links only | Operators run the formal outreach, but your evidence helps them find the right contacts. |
| The proposed release: version number, source commit or the branch or pull request it will come from, what changed since the previous release, and which platform builds it needs | The grant covers exactly these files and nothing else. |
| Whether the release is security-motivated, and the public advisory if it is | Security grants require an advisory. |
| The proposed grantee's RubyGems.org and source-host account names | The grantee must have merge rights, an account in good standing, and MFA on both accounts. |
| A proposed technical reviewer, if you have one | Someone other than the grantee must review the changes and the built gem files. |
| Any conflicts of interest | Approving operators must be independent of the request. |

By opening a request, the requester and grantee agree to be identified in this log by their public account names.

### What happens next

1. **Outreach.** Operators make one contact attempt to every existing owner and relevant organization administrator, through their RubyGems.org account email and, separately, the gemspec author email if it differs.
   Alongside that attempt, operators open a public notice issue on the gem's canonical repository.
   Each contact has at least 14 days after the attempt to respond, and no grant can take effect until every contact's deadline has passed.
   Operators may also weigh GitHub activity and other sources when judging whether an owner is available.
   You do not need to contact the owners yourself.
2. **Owner responses.** A verified reply from an owner pauses the request while operators clarify what the owner wants.
   A verified refusal closes the request.
3. **Review.** A technically qualified person other than the grantee reviews the changes and the final built gem files, and the test suite must pass.
4. **Approval.** Two independent RubyGems.org operators approve the grant, its scope, and the exact gem files by checksum.
5. **Activation.** Operators issue the API key, and the grantee publishes the approved files within 72 hours, with MFA on every upload.
6. **Record.** The outcome, including any corrective release or revocation, is added to the grant record.

In an active-exploit emergency, two independent operators may shorten the 14-day response period and record why; every other condition still applies.

There is no formal appeal.
A refused request may be resubmitted with new facts.

## How operators record decisions

Each request issue is the running public log of that request: outreach dates and response deadlines, owner responses (summarized, never quoted), operator questions, and the decision.

Every decision also gets a permanent record file in this repository, added by pull request:

```
records/
  <gem-name>/
    <issue-number>.md
templates/
  grant.md
  refusal.md
```

- **Grant:** copy [`templates/grant.md`](templates/grant.md) to `records/<gem-name>/<issue-number>.md` and fill it in.
  Merge it before access is activated, then update it by further pull requests with activation, publication, and any correction or revocation.
- **Refusal or closure:** copy [`templates/refusal.md`](templates/refusal.md) to the same path and fill it in.
  This covers operator refusals, verified owner refusals, requests resolved through existing access, and withdrawn requests.
- **Private security requests:** once the advisory is public, open an issue for the request, then add its record as above.

When the record is merged, link it from the request issue and close the issue.
