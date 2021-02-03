# Github Labels

## General

[Tool Repository](https://github.com/popomore/github-labels#readme)

Adds github labels automatically.

It's very useful that init all your custom labels when create a repo.

## How To Use Labels

This guide is based on this [styleguide](https://robinpowered.com/blog/best-practice-system-for-organizing-and-tagging-github-issues).

For clarity, use only **one** of these labels! if you feel that you need to use more, your issue might not be specific enough:

* `#EE3F46` Problems (high priority): `bug` `security` `production`
* `#5EBEFF` Improvements (generally iteration on code): `enhancement` `optimization`
* `#91CA55` Additions (generally new code): `feature`
* `#CC317C` Feedback (some do not involve code): `discussion` `question` `community`
* `#FAD8C7` Environment (needs to be done or only occurs in): `test` `staging`
* `#FFC274` Experience (more artistic): `design` `ux`
* `#FEF2C0` Mindless (can be done during a break): `chore` `legal` `documentation`
* `#D2DAE1` Inactive (gets immediately closed): `invalid` `wontfix` `duplicate` `deprecated`

Optionally: These can be attached to the ones above to give more context:

* `#BFD4F2` Platform (can exceptionally be customized to group issues): `server` `browser` `android` `ios` `web` 
* `#FBCA04` State (stalled by difficulty or external): `help wanted` `in progress` `on hold` `watchlist`

**Label Groups**

Your should group labels by color, according to broad themes. Labels are consistent across repositories, except for a few language specific topics. This makes switching between projects easy, since you don't need domain expertise in order to write an issue. New team members can learn the system once, and use it everywhere.

**Problems**

Issues that make the product feel broken. High priority, especially if its present in production.

**Improvements**

Iterations on existing features or infrastructure. Generally these update speed, or improve the quality of results. Adding a new “Owner” field to an existing “Calendar” model in the API, for example.

**Additions**

Brand new functionality. New pages, workflows, endpoints, etc.

**Feedback**

Requires further conversation to figure out the action steps. Most feature ideas start here.

**Environment**

Server environment. With good QA, you’ll identify issues on test and staging deployments.

**Experience**

Affect user’s comprehension, or overall enjoyment of the product. These can be both opportunities and “UX bugs”.

**Mindless**

Converting measurements, reorganizing folder structure, and other necessary (but less impactful) tasks.

**Inactive**

No action needed or possible. The issue is either fixed, addressed better by other issues, or just out of product scope.See a version of this in action on one of our public repos. Want to see what we're building? Check out our product features.

**Platform**

If the repository covers multiple parts, this is how we designate where the issue lives. (i.e. iOS or Android).

**State**

The State of an Issue i.e. Help Wanted or On Hold.

---

## Install

```
$ npm install github-labels -g
```

## Usage

```
$ labels -c path/to/conf.json user/repo
```

About config file, see [my conf](https://gist.github.com/popomore/8ef8ad0573c97081da22dca1cc84173e) for example.

```
[
  {"name": "bug", "color": "ffffff"},
  {"name": "feature", "color": "000000"}
]
```

Your can simplify it that will generate github default color automatically.

```
["bug", "feature"]
```

Force option will delete all existing labels, otherwise will create label when not exist or update label when existing label has different color.

```
$ labels -c path/to/conf.json -f user/repo
```

## GitHub Enterprise configuration

If you're using a GitHub Enterprise instance, you'll need to pass some additional parameters to target your environment
* `host` - The hostname of your GHE instance.
* `pathPrefix` - The path to the API. Frequently for GHE this will be `/api/v3`.

```
$ labels -c path/to/conf.json -h github.myhost.com -p /api/v3 user/repo
```

You can also provide the OAuth token to be used directly via the `--token` parameter. 
This is useful when your GHE environment does not allow user/pass login.

```
$ labels -c path/to/conf.json -h github.myhost.com -p /api/v3 -t PERSONAL_TOKEN_123 user/repo
```

### Export from GitHub website

Here is a snippet to be able to export github labels from the labels page of a project

[gist.github.com/MoOx/93c2853fee760f42d97f](https://gist.github.com/MoOx/93c2853fee760f42d97f)

Running this code in your browser console should output your some json ready to be imported.
