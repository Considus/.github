# Review context for Considus repositories

The automatic Claude review in every Considus repository appends this file to its prompt. It holds facts a reviewer cannot see from one diff, each one added because a review got it wrong. Keep each entry to what changes a finding.

## Dates are UK time

The studio works in Europe/London. A date in a CHANGELOG, a commit or a PR that is one day ahead of UTC is today in London, not a future date. Do not report it.

## Check a claim about platform support before making it

Before reporting that a browser, OS, runtime or tool ignores or lacks a feature, be sure the claim holds for current versions. If you cannot verify it, say it is unverified rather than stating it. Known case: `media` on a `<source>` inside `<video>` is honoured by Chrome and Firefox 120 and later and by Safari, so "browsers ignore it" is wrong.

## One change often spans two repositories

A generator lives in an Ops repo and its built output in a site repo; some scripts and Pages Functions are deliberate copies in two repos, each guarded by a parity check. When the PR description names the other repository's PR for part of the change, take that part as given: do not report it as missing from this diff. This review cannot read other private repositories.
