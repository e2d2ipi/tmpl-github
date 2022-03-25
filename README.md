# GitHub Project Shelf

This template is agnostic to the programming language used. GitHub Actions manage issues and pull requests, while a generic filesystem, third party tools and a detailed description of robust workflow model help enforcing best practices.

[![GitHub issues](https://img.shields.io/github/issues/e2d2ipi/tmpl-github-project.svg)](https://github.com/e2d2ipi/tmpl-github-project/issues)
[![GitHub forks](https://img.shields.io/github/forks/e2d2ipi/tmpl-github-project.svg)](https://github.com/e2d2ipi/tmpl-github-project/network)
[![GitHub stars](https://img.shields.io/github/stars/e2d2ipi/tmpl-github-project.svg)](https://github.com/e2d2ipi/tmpl-github-project/stargazers)
[![GitHub license](https://img.shields.io/github/license/e2d2ipi/tmpl-github-project.svg)](https://githubcom/e2d2ipi/tmpl-github-project/blob/main/LICENSE.md)

## Why use a template (even for small projects)

- Increase [security](#security)
- Follow recognized [ethical principles](#ethics)
- Promote [Free and Open-source software](#foss)
- Write more [consistent](#consistency) code and foster collaboration
- Write better [documentation](#documentation) for you and the community

## How this template helps you with this

### Documentation

- [package.json](package.json) according to [npm docs](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- Accessible documentation via [gh-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)
- Automated [CHANGELOG.md](CHANGELOG.md) via [git-cliff](https://github.com/orhun/git-cliff)
- [README.md](README.md) according to [www.makeareadme.com](https://www.makeareadme.com/)
- [CHANGELOG.md](CHANGELOG.md) according to [keepachangelog.com](https://keepachangelog.com/)

### Consistency

- Consistent issues via [issue templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
- Consistent labels for pull requests via [labeler](https://github.com/actions/labeler)
- Consistent versioning via [Semantic Versioning](https://semver.org/spec/v2.0.0.html)
- Consistent formatting via [Prettier](https://prettier.io/) and [markdownlint](https://github.com/DavidAnson/markdownlint)
- Consistent [fork and pull](https://gist.github.com/Chaser324/ce0505fbed06b947d962) workflow via [GitHub branch protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)
- Consistent commit messages according to [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) via [husky](https://github.com/typicode/husky) and [commitizen](https://github.com/commitizen/cz-cli)
- Consistent workflow using well documented versatile [Guidelines and Conventions](./[dev/docs/framework-model.doc.md])
- Consistent file organisation across projects via a generic Foler Structure
  (see _.gitkeep_ files).

### Security

- [GitHub security alerts](https://github.blog/2017-11-16-introducing-security-alerts-on-github/)
- [SECURITY.md](SECURITY.md) according to [GitHub](https://docs.github.com/en/code-security/getting-started/adding-a-security-policy-to-your-repository)
- Integrity via [GitHub branch protection](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule)

### Ethics

- Friendly first interactions via [greetings](https://github.com/actions/starter-workflows/blob/main/automation/greetings.yml)
- [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) according to [Contributor Covenant](https://www.contributor-covenant.org/)

### FOSS

- [LICENSE.md](LICENSE.md) according to [choosealicense.com](https://choosealicense.com/)

## Installation

To initialize the template, [generate](https://github.com/e2d2ipi/tmpl-gas-ts-project/generate) a new repository from the current template and follow the instructions below:

### 1. Activate Github's features

- [ ] Activate [GitHub security alerts](https://github.blog/2017-11-16-introducing-security-alerts-on-github/)

- [ ] Activate [gh-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) (mater's root level)

- [ ] [Protect](https://help.github.com/en/articles/configuring-protected-branches) branches to enforce a [fork and pull](https://gist.github.com/Chaser324/ce0505fbed06b947d962) workflow  
(all of `main`, `master`, `dev` and `develop` can be protectected at the same time using the following pattern: `[dm][ea][vis]*`)

### 2. Replace `TAGS` across the template

The first step in customizing this template consists in replacing `TAGS` by your own data in various files

> **Note.** Performing a global _Find & Replace_ across all (original) templates' files is safe.

#### 2.1. Replace tags `USER` and `REPO` by your (GituHub) _Username_ and _Repository name_ in the following files

- [ ] [cliff.toml](./cliff.toml)
- [ ] [CHANGELOG.template.md](./RSECURITY.template.md)
- [ ] [package.json](package.json)
- [ ] [README.template.md](./README.template.md)
- [ ] [SECURITY.template.md](./RSECURITY.template.md)

#### 2.2 In [README.template.md](./README.template.md), further provide

- [ ] A `SHORT_DESCRIPTION` of your project
- [ ] Your `FULLNAME` or this of the project's main contributor(s)

#### 2.3. In [package.json](package.json), specify

- [ ] A `VERY_SHORT_DESCRIPTION` of your project
- [ ] The main author's data, namwly
- The `AUTHOR_NAME`
- The `AUTHOR_EMAIL`
- The `AUTHOR_URL`

#### 2.4. In [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md) , provide

- [ ] A `CONTACT_METHOD`

### 3. License your project

- [ ] Choose an appropriate license with [choosealicense.com](https://choosealicense.com/)

- [ ] Update [README.template.md](README.template.md) and [LICENSE.md](LICENSE.md) accordingly

### 4. Install Node.js and the template's features

- [ ] Install the [latest LTS or higher version of Node](https://nodejs.org/en/download/) and [npm](https://www.npmjs.com/)

- [ ] Install [pnpm](https://pnpm.io/) globally

  ```bash
  npm install -g pnpm;
  ```

- [ ] Install [Commitizen](https://github.com/commitizen/cz-cli) globally and initialie your project to use it (may require using the --force option)

  ```bash
  npm install -g commitizen;
  commitizen init cz-conventional-changelog --save-dev --save-exact;
  ```

- [ ] Install all other dependancies defined in [package.joon](/package.jon)

  ```bash
  npm install;
  npm run prepare;
  ```

### 5. Clean and Customize

- [ ] Remove [SECURITY.md](./SECURITY.md) from root foler.  
       Rename [SECURITY.template.md](./SECURITY.template.md) to "SECURITY.md".

- [ ] Remove [CHANGELOG.md](./CHANGELOG.md) from root foler.
      Rename [CHANGELOG.template.md](./CHANGELOG.template.md) to "CHANGELOG.md".

- [ ] Remove [README.md](./README.md) from root foler.  
       Rename [README.template.md](README.template.md) to "README.md".

## Usage

Check if all files are formatted correctly.

```bash
npm run check
```

Format all files.

```bash
npm run format
```

Run the wizard to write meaningful commit messages.

```bash
npm run commit
```

## Support

This project is maintained by [@e2d2ipi](https://github.com/e2d2ipi). Please understand that we won't be able to provide individual support via email. We also believe that help is much more valuable if it's shared publicly, so that more people can benefit from it.

| Type                                  | Platforms                                                                     |
| ------------------------------------- | ----------------------------------------------------------------------------- |
| 🚨 **Bug Reports**                    | [GitHub Issue Tracker](https://github.com/e2d2ipi/tmpl-github-project/issues) |
| 🎁 **Feature Requests**               | [GitHub Issue Tracker](https://github.com/e2d2ipi/tmpl-github-project/issues) |
| 🛡 **Report a security vulnerability** | [GitHub Issue Tracker](https://github.com/e2d2ipi/tmpl-github-project/issues) |

## Roadmap

No changes are currently planned.

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors and acknowledgment

- **Stefano Picozzi, [e2d2ipi](https://github.com/e2d2ipi)** - _Initial work_

See also the list of [contributors](https://github.com/e2d2ipi/tmpl-github-project/graphs/contributors) who participated in this project.

Credits to [M. Maher's](https://github.com/e2d2ipi) whose [github-template](https://github.com/maehr/github-template) served as base for the present work and is the source of most of the available functionalities.

> If you find this template well done and useful, consider having a look at **[M. Maher's](https://github.com/e2d2ipi)** own repositories. Also, please, **do not star the present repository without starring [his](https://github.com/maehr/github-template)&nbsp;**!

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE.md](LICENSE.md) file for details
