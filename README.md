# mattpocock-skills-marketplace

A thin [omp](https://github.com/can1357/oh-my-pi) marketplace wrapper for [Matt Pocock's skills](https://github.com/mattpocock/skills), release-tracked so the plugin auto-updates to tagged releases.

## Why a wrapper

Matt's own `.claude-plugin/marketplace.json` catalog entry has **no `version` field**, and omp's update detector reads only that field — so `autoUpdate: auto` would silently skip `mattpocock-skills` forever. This wrapper pins the GitHub source to a release `ref` and declares a matching `version`; a [release-watching action](.github/workflows/watch-release.yml) bumps both whenever Matt tags a new release.

## Install

Add the marketplace, then install the plugin at user scope:

```bash
omp plugin marketplace add calvertjadon/mattpocock-skills-marketplace
omp plugin install mattpocock-skills@mattpocock-skills-marketplace --scope user
```

Or from inside omp with slash commands:

```
/marketplace add calvertjadon/mattpocock-skills-marketplace
/marketplace install mattpocock-skills@mattpocock-skills-marketplace --scope user
```

## Auto-update

Enable auto-update (global setting; applies upgrades once per startup):

```bash
omp config set marketplace.autoUpdate auto
```

When the wrapper's `version` field advances — the watch action bumps it on each Matt release — omp upgrades the plugin automatically.

## What's included

The 25 skills published by `mattpocock/skills`: engineering (`wayfinder`, `domain-modeling`, `tdd`, `code-review`, `prototype`, `research`, …) and productivity (`grilling`, `grill-me`, `handoff`, `teach`, `writing-for-agents`, …).
