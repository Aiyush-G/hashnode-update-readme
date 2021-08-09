<h3 align="center">📡📝</h3>
<h3 align="center">Hashnode RSS to README Action</h3>
<p align="center">A GitHub Action that updates a section of a README from a Hashnode RSS feed.</p>

---

## Usage

You can use this action in a workflow file like any other:

```yml
name: Update this repo's README

on:
  schedule:
    # Once a day at 8 AM
    - cron: 0 8 * * *
    
# To manually run uncomment the line below and comment/delete out the `on` above
# on: workflow_dispatch

jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - uses: Aiyush-G/hashnode-update-readme@v1
        with:
          feed-url: https://ooshimus.com/rss.xml
          readme-section: hashnode
```

### Options

#### `feed-url`:

The URL to an RSS feed. It's assumed that the RSS feed follow the standard format!

#### `readme-section`:

The name of the section of your README to update. This uses [`JasonEtco/readme-box`](https://github.com/JasonEtco/readme-box) to replace a section of the README and update the file. Your README should contain HTML comments like this, where `feed` is the the value of `readme-section`:

### Example RSS feed from Ooshimus.com:

<!--START_SECTION:hashnode-->
* [Console.log() - The Right Way ✅](https:&#x2F;&#x2F;ooshimus.com&#x2F;consolelog-the-right-way)
* [Is GPT-3 still King? Introducing GPT-J-6B](https:&#x2F;&#x2F;ooshimus.com&#x2F;is-gpt-3-still-king-introducing-gpt-j-6b)
* [From GhostCMS to Hashnode](https:&#x2F;&#x2F;ooshimus.com&#x2F;from-ghostcms-to-hashnode)
* [Printing COLOUR in IDLE in less than 2 minutes!](https:&#x2F;&#x2F;ooshimus.com&#x2F;printing-colour-in-idle-in-less-than-2-minutes)
* [Controlling A Website with a TV Remote!!!](https:&#x2F;&#x2F;ooshimus.com&#x2F;controlling-a-website-with-a-tv-remote)
<!--END_SECTION:hashnode-->


You can inspect this repo's README to see it in use!

#### `max` (default: 5)

The maximum number of items to show from the RSS feed. Defaults to `5`!

#### `template` (default: `"* [{{ title }}]({{ link }}))"`)

You can provide a [Mustache](https://github.com/janl/mustache.js) template to use when rendering each item in the feed. These will be joined by a newline (`\n`). For example:

```yaml
- uses: JasonEtco/rss-to-readme@v1
  with:
    feed-url: https://jasonet.co/rss.xml
    template: "> {{ excerpt }}\n\n[Read more!]({{ url }})"
```

#### `branch` (default: github.repository.default_branch)

You can provide the target branch to update instead of the default.

### Example RSS feed:

<!--START_SECTION:example-->

<!--END_SECTION:example-->

> Credit to JasonEtco for inital design!
