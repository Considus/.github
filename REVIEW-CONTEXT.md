# Review context for Considus repositories

The automatic Claude review in every Considus repository appends this file to its prompt. It holds facts a reviewer cannot see from one diff, each one added because a review got it wrong. Keep each entry to what changes a finding.

## Dates are UK time

The studio works in Europe/London. During British Summer Time (late March to late October) London is one hour ahead of UTC, so between 00:00 and 01:00 BST a CHANGELOG, commit or PR date is already the next day in UTC terms. Before reporting a date as in the future, check it against today's date in Europe/London; if it matches, it is not a finding. A date later than that is.

## Check a claim about platform support before making it

Before reporting that a browser, OS, runtime or tool ignores or lacks a feature, be sure the claim holds for current versions. If you cannot verify it, say it is unverified rather than stating it. Known case: `media` on a `<source>` inside `<video>` was measured on 2026-10-09 to be honoured by Chrome 152 (a 375px viewport picked the 720p source, a 930px one the 1080p source), so "browsers ignore it" is wrong for Chrome. For any other browser or version, verify before claiming either way.

## One change often spans two repositories

A generator lives in an Ops repo and its built output in a site repo; some scripts and Pages Functions are deliberate copies in two repos, each guarded by a parity check. When the PR description names the other repository's PR for part of the change, do not report that part as missing from this diff: this review cannot read other private repositories. Do flag it when the description's own account of the other PR does not cover the part in question, or when nothing names where it lives.
