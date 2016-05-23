# How to translate bem.info

We've got two parts: interface and content.

Everything is in open source on github.

Here's an example of how interface translations are kept: [github.com/bem-site/bem.info/blob/master/blocks/index/footer/footer.i18n/en.js](https://github.com/bem-site/bem.info/blob/master/blocks/index/footer/footer.i18n/en.js).

Content is stored in [github.com/bem/bem-method](https://github.com/bem/bem-method) as markdown files with lang extentions. E.g. [github.com/bem/bem-method/blob/bem-info-data/method/key-concepts/key-concepts.en.md](https://github.com/bem/bem-method/blob/bem-info-data/method/key-concepts/key-concepts.en.md).

But we can't just translate these files and create pull requests because otherwise it'll be very hard to maintain updates.

So we need tooling to help us automate translation and get possibility to invalidate only updated parts.

There's a standard for it called [XLIFF](https://en.wikipedia.org/wiki/XLIFF).

In short:

1. Source content is splitted by phrases and stored in XLIFF format with additional file called `skeleton`.
2. Each phrase is translated separately in XLIFF.
3. Source structure is recreated with the help of `skeleton`.

So it looks like this: `article.en.md -> [ article.xliff, article.skl ] -> article.es.xliff -> article.es.md`.

We've got [some scripts](https://github.com/tadatuta/md2xliff) to do it but there's still some issues with them.

So for now we can translate the site this way:

1. We generate and commit XLIFFs to https://github.com/bem-site/translation repo.
2. People who want to help with translation fork the repo and make translations. Then send PRs to source repo
3. We generate translated markdowns and publish on bem.info.

In the future we'll create web interface for such translations.
