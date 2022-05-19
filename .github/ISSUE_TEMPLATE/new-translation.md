---
name: Request new translation
about: Request to add a new translation
labels: language
---

<!--
Make sure there isn't an existing issue with the language you request to add.
-->

Language:

<!--
Replace this comment with a short introduction of yourself and your former experience with Flask and translation (English -> your language).
-->

<!--
To become a translation coordinator and create a translation for your language, please complete the following initial tasks in 30 days:
-->

## Initial tasks
- [ ] Create an empty repository on GitHub. Name the repository as `flask-docs-<lang code>`, for example, `flask-docs-es`.
- [ ] Set up your repository based on the translation template repository:
```
$ git clone https://github.com/flaskcwg/translation-template.git flask-docs-<lang code>
$ cd flask-docs-<lang code>
$ git remote set-url origin <the-Git-URL-to-your-repository>
$ git remote add upstream https://github.com/pallets/flask.git
$ git fetch upstream
$ git merge upstream/2.1.x
$ git push -u origin main
```
- [ ] Create a virtual environment, then install the requirements:
```
$ python -m pip install --upgrade pip setuptools
$ pip install -r requirements/dev.txt
$ pip install sphinx-intl
$ pip install -e .
$ pre-commit install
```
- [ ] Generate the `.pot` and `.po` files (replace `<lang code>` with your language code):
```
$ cd docs
$ make gettext  # use ".\make.bat gettext" on Windows
$ sphinx-intl update -p _build/gettext -l <lang code>
```
- [ ] Replace the `<LANG>` in the `README.md`, the `language` config, and the
`html_search_language` config in `docs/conf.py` with your language code.
Update the `.po` file examples.
- [ ] Setup ReadtheDocs to connect your repository, use `flask-<lang code>` as the subdomain, set the default version to the `main` branch, and enable the "single version" mode.
- [ ] Translate the `README.md` and the pull request template (optional).
- [ ] Update the title, and all the `<UPDATE THIS>` placeholders  in `README.md` and `docs/conf.py`. You can update the `README.md` to add more format or translate tips for your language.
- [ ] [Optional] You can choose to use [Transifex](https://www.sphinx-doc.org/en/master/usage/advanced/intl.html#using-transifex-service-for-team-translation) or other translation platforms. In that case, you will need to rewrite the "Contributing Guide" in the `README.md`.
- [ ] Update the `Language-Team` field value in all `.po` files with your language code and email.
- [ ] Translate `html_title` and project links in the `docs/conf.py` file.
- [ ] Translate the `docs/index` file (you can make a localized logo for the index page).
- [ ] Translate the `docs/foreword` file.
- [ ] Translate the `docs/advanced-foreword` file.
- [ ] Translate the `docs/installation` file.
- [ ] Translate the `docs/quickstart` file.
- [ ] Translate the "Tutorial" part of the docs.
- [ ] Switch the repository into the flaskcwg organization. See [HERE](https://flaskcwg.github.io/faq/migrate-repo-to-flaskcwg-org/).

<!--
We recommend you finish the translation of the chapters above by yourself to keep the
quality and reading experience of the essential part of the documentation. These
chapters are marked as reserved in the translation to-do list.
-->

<!--
When you finished the tasks above, leave a comment that includes your repository URL to ping us, we will switch your repository into the flaskcwg organization, then you can work on other chapters or call for other people to contribute.

After that:
-->

## Public

Tasks after the repository is switched into flaskcwg:

- [ ] Add a new language entry to [the README](https://github.com/flaskcwg/translation-coordination/blob/main/README.md).
- [ ] Add a new language entry to [translations page](https://github.com/flaskcwg/flaskcwg.github.io/blob/source/templates/translations.html).


## Maintenance

Tasks when the whole documentation is translated:

- [ ] Create a 2.1.x branch, set it as default version on ReadtheDocs.
- [ ] Rewrite the contributing guide in the `README.md` of the translation repository, encourage people to fetch upstream and update docs (see details below).
- [ ] Rename the section "Translation To-do List" to "Translators". You can also add
a "Reviewers" section.
- [ ] Switch the docs into http://flask.palletsprojects.com/.

You should sync documentation updates from Flask periodically:

```
$ git fetch upstream
$ git merge upstream/2.1.x
$ cd docs
$ make gettext  # use ".\make.bat gettext" on Windows
$ sphinx-intl update -p _build/gettext
```

Then update the translation for new changes.
