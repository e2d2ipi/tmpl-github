# GitFlow, Versions and Changelog

<!-- markdownlint-disable MD033 -->

<details>
  <summary>Table of Contents</summary>

- [GitFlow, Versions and Changelog](#gitflow-versions-and-changelog)
  - [Versioning](#versioning)
  - [Changelog](#changelog)
  - [Committing changes](#committing-changes)
    - [Commit's type](#commits-type)
    - [Commits' scope](#commits-scope)
    - [Commit's subject](#commits-subject)
    - [Body](#body)
    - [Footer](#footer)
  - [GitFlow model](#gitflow-model)
    - [Initalization](#initalization)
      - [(I) Initialize `master` branch (v0.0.1)](#i-initialize-master-branch-v001)
      - [(II) Instantiate `develop` branch](#ii-instantiate-develop-branch)
      - [(III) Work on `develop` and/or start a `feature` branch](#iii-work-on-develop-andor-start-a-feature-branch)
    - [Hotfix](#hotfix)
      - [(I) Start a hotfix](#i-start-a-hotfix)
      - [(II) Work out the patch](#ii-work-out-the-patch)
      - [(III) Terminate the hotfix](#iii-terminate-the-hotfix)
    - [Feature](#feature)
      - [(I) Start developping a new feature](#i-start-developping-a-new-feature)
      - [(II) Work out the new feature](#ii-work-out-the-new-feature)
      - [(III) Terminate the new feature](#iii-terminate-the-new-feature)
    - [Release](#release)
      - [(I) Start a new release](#i-start-a-new-release)
      - [(II) Test and deebug the new release](#ii-test-and-deebug-the-new-release)
      - [(III) Terminate the new release](#iii-terminate-the-new-release)

</details>
<!-- markdownlint-enable MD033 -->

This document suggests an implementation of the well established standarts that exist in the matter of [GitFlows](https://en.wikipedia.org/wiki/Git), [Sofware Versionning](https://en.wikipedia.org/wiki/Software_versioning) and [Changelogs](https://en.wikipedia.org/wiki/Changelog) that is well suited for small projects.

> **Devlopper's Golden Rules**  
> &starf;&nbsp;&nbsp;Commit often  
> &starf;&nbsp;&nbsp;Do not get stuck more than 5 min  
> &starf;&nbsp;&nbsp;Partition projects into small, reusable, chunks

Regarding Git, it is based on the standard 5 branches - `master`, `develop`, `hotfix`, `feature` and `release` - architecture implemented in [SourceTree](https://www.sourcetreeapp.com/) and which concepts are described in great details in [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/).

> **Note.** _The Git Flow model described here was explicitely designed such that it matches the default behavior of SourceTree. As a consequence, SourceTree's integrated macros will generate non-conflicting outputs and should be used whenever possible._

The suggested versioning model is a simplified version of [Semantic Versioning](http://semver.org/) where detailed attributes such as _builts_ or _alpha/beta_ releases is abandonned to keep only the main 3 didgits syntax `x.y.z`.

Finally,proposed method to mantain a version's history is to keep track of the main changes in a [CHANGE_LOG](CHANGE_LOG.md) file, as described in [Keep a changelog](https://keepachangelog.com/en/1.0.0/).

## Versioning

The versionning follows the standards of [Semantic Versioning](http://semver.org/). As the model described here is meant for small developments, there is no mean to subversion the project using builds, nor even preleases. In other words, it sticks to the standard 3 integers format `X.Y.Z`.

In the following, brackets are used to specify an element which differs from the last version which was released, or to point out at one which was just changed. For example, `X.Y.<Z>` is used to notigy that the PATCH version `Z` has been modified compared to to the previous version (in that particular it was typically incremented by 1). Similarly, `<X>.<Y>` means that (at least one of) `X` and `Y` have been modified.

## Changelog

The main changes from one version to the other are documented in a file named [CHANGE_LOG](CHANGE_LOG.md) which references the main changes from one version to the other. Past the additional "Improved" section, the Changelog define here after is formatted as advised in [Keep a changelog](https://keepachangelog.com/en/1.0.0/). A typical version block is as follows:

```text
## [vers](https://PATH_TO_REPO/(tag/<tag>|compare/<base>...<curr>)) - yyyy-mm-dd

### Added
  - For newly added features

### Changed
  - For changes in existing functionalities

### Deprecated
  - For soon to-be-removed features

### Removed
  - For now removed feadtures

### Fixed
  - For bug corrections

### Security
  - For vulnerability fixes
```

## Committing changes

[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification) is a popular lightweight convention on top of commit messages which can easily be enforced using tools like [commitlint](https://github.com/conventional-changelog/commitlint) or [Commitizen](http://commitizen.github.io/cz-cli/). Sticking to this normalied syntax not only makes commits more readable, but it also **makes it much easier for algorithms to parse commits** and, thus, automatically generate useful documentation such as Changelogs. Accoding to these standards, messages should be formatted as follows:

```text
<type>[(scope)][!]: <subject>

[body]

[footer(s)]
```

A complete list of the "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" is decribed in full details in [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification).

### Commit's type

[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification) standards explicitely identify only 2 types, namely `feat` and `fix`. Using additional ones is left up to everyone to choose according to their needs.

> **Note.** _The types below match the defaults of [Commitizen](http://commitizen.github.io/cz-cli/), which are themselves based were inpired by [Angular conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#heading=h.uh9jqqu4fjy3) and the guidelines to [Contributing to Angular](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)_.

The typical list of the `types` to stick to is as follows:

- [ ] `fix` for bug fixes

- [ ] `feat` for new features

- [ ] `docs` for documentation only changes

- [ ] `perf` for modifications improving performances

- [ ] `refactor` for changes that neither add a feature nor fix a bug

- [ ] `security` for changes patching identified vulnerabilities

- [ ] `style` for changes not affecting the meaning of the code (formatting, missing semi colons, white-space, ...)

- [ ] `test` when adding or modifying tests

- [ ] `build` for changes to the build process or external dependencies

- [ ] `chore` for other changes that do not modify src or test files

### Commits' scope

The scope can be anything specifying the place of the commit change. Possible scopes obviously depend on the `type` of the commit and can be as different as a symbol's name, the path to a section of the documention or placeholder within a template.

According to the specifications of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification), specifying a scope is optional. However, consider using \* instead of skipping it, especially in the case when the difficulty to find a fitting one is that the change concerns multiple scopes.

### Commit's subject

The subject contains a succinct description of the change. It is expected to respect the following formatting rules:

- No dot (.) at the end
- Use imperative, present tense
- Do not capitalize the first letter

Conventional Commits' specifications impose no limitationss on the length of subjects. However, it is common practice to not exceeed 50 characters and libraries such as [Commitizen](http://commitizen.github.io/cz-cli/) even strictly enforce it by default.

> **Note.** _When a modification "silently" impacts the code in more than one way that would (e.g. a new features which addition deprecates another one), consider highlighting each significant alteration of the code with its own commit. For,  make (and commit) changes on code comments._

Past these conventions, a Commit's subject can be freely worded. Stil, trying to be as consistent as possible when phrasing subjects and using meaningful verbs to describe the action that was taken is worth some special attention.

### Body

Just as in the subject, use the imperative, present tense: "change" not "changed" nor "changes". The body should include the motivation for the change and contrast this with previous behavior.

### Footer

The footer should contain any information about Breaking Changes and is also the place to reference GitHub issues that a commit Closes.

Breaking Changes should start with the word BREAKING CHANGE: with a space or two newlines. The rest of the commit message is then used to describe the change (including an explanation on how to migrate the code).

<!--
## Changelog's Automation

One of the goals of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification)  is to allow to algorithmically generate documentation such as [Changelog](#changelog) files directly from the content of the Commits that were written throughout the development. Libraries sucg as [git-cliff](https://github.com/orhun/git-cliff) provide tools to parse commits messages into structured objeccts that can then be used to build up well formatted file using templates. However, generating a clean document without having to implement complex parsers requires some more conventions than just the formatting rules of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification). It is in particular essential to be able to easily determine which among all commit messages are the ones meant to generate entries in the Changelog file and how they then map to the different sections of that file.

The next setions describe a strategy simplifying the extraction of meaningful and consistent information from [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification). As an example of how commits following this strategy can be parsed to a standard Changelog file using git-cliff, see [cliff](../../cliff.toml) .

### Commits generating an entry in the Changelog file

Unless being ready to implement complex parsers, committing often and getting a cleaan, nonredundant, Changelog file are quite incompatible expectations. Also, generating a document based on commit messages written by different developpers has very few, if any at all, chances to end up with a consistent, easy to read and comprehend, document. A solution to both issues consists in focussing only on the commits done on a specific, protected, branch.

Within the GitFlow model described [below](#gitflow), the most

### Assigning a commit to a Changelog's section

### Link Commits to Changelog's sections

The key to alorithmically generating a Changelog - or any similar documentation - from  Commit messages stands into ensuring coherent and unequivocally parsable content of the commits. In order to avoid implementing very complex parsers, additional conventions should be added to these of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/#specification). Also,

> > &nbsp;
> >
> > > **@todo This is is still to be fomalized**
> > >
> > > **@todo Improve the way conventional commits are used in the next section**
> > >
> > > &nbsp;
-->

## GitFlow model

The GIT Workflow described in [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/) is particularly adapted to small to medium projects and is widely used. This model can be decomposed into four distinct actions, namely

- [Intialization](#initialization) - seeding a new project,
- [Hotfix](#hotfix) - patching a released version,
- [Feature](#feature) - implemeting and integrating of a new feature and
- [Release](#release) - releasing a new maor or minor version.

The next sections detail the steps to take in each case, how to commit the changes and, which can be ignored if relying on an automatically generated one, how to manually maintain Changelog accordingly.

### Initalization

We assume that a repo which main branch is `master` was created from scratch or generated from an exiting template, which GitHub automatically commits as `Ìnitial Commit`. Such seeded project tyically contains a basic README file and a LICENSE.

#### (I) Initialize `master` branch (v0.0.1)

- [ ] If needed, Setup/Update the project's core structure.

    ```text
    COMMIT:
    chore(*): ...
    ```

- [ ] Tag as version `v0.0.1` (NOT a release)

    ```text
    [TAG] v0.0.1
    ```

- [ ] Changelog: reset/initialize the file

    ```text
    CHANGE_LOG:
    ## [0.0.1](https://PATH_TO_REPO/releases/tag/v0.1.0) - <yyyy-mm-dd>

    COMMIT:
    chore(*): initialize 'CHANGE_LOG file' by declaring 'v0.0.1'
    ```

#### (II) Instantiate `develop` branch

- [ ] Create branch `develop` from `master`

- [ ] Changelog: pre-declare the next _unreleased_ version

    ```text
    CHANGE_LOG:
    ## [Unreleased](https://PATH_TO_REPO/compare/0.0.1...develop)

    COMMIT:
    chore(*): initialize 'next release' after 'v0.0.1'
    ```

#### (III) Work on `develop` and/or start a `feature` branch

&nbsp;&nbsp;&nbsp;&#9755;&nbsp; Prefer working on a feature branh whenever possible!  

- [ ] When working on `develop` , commit changes as described in [Committing changes](#committing-changes)

- [ ] For how to start `feature` branch, see section [Faeture](#feature).

- [ ] For how to patch `master` without waiting for a release, see [hotfix](#hotfix)

### Hotfix

Hotfixes are used to patch the `master`'s HEAD version. They branch from the `master` branch and merge in both `master` and `develop`. Would a pre-release be in progress, the patch should also be merged into evey related branch.

Merging a `hotfix` into the `master` causes the PATCH version of the project to be incremented by one. That new version number is used to name the `hotfix` branch: if the release to patch is versioned `X.Y.Z`, then the hotfix's branch is named `hotfix/vX.Y.<Z>`.

#### (I) Start a hotfix

- [ ] Create branch `hotfix/vX.Y.<Z>` from `master`

- [ ] Changelog: initialize the patch's block

  ```text
  CHANGE_LOG:
  ## [hotfix/vX.Y.<Z>](https://PATH_TO_REPO/compare/vX.Y.Z...hotfix\/vX.Y.<Z>)

  COMMIT:
  chore(*): initialize 'hotfix/vX.Y.<Z>'
  ```

#### (II) Work out the patch

- [ ] No merge wherever until the fix is complete

- [ ] Make the correction and update the Changelog accordinly

- [ ] Commit changes as described in [Committing changes](#committing-changes)

  ```text
  COMMIT:
  fix(...): ... OR security(...): ...
  ```

#### (III) Terminate the hotfix

- [ ] Changelog: Finalize `[hotfix/vX.Y.<Z>]` and let `[unreleased]` compare to the patched version

  ```text
  OLD CHANGE_LOG:
  ## [hotfix/vX.Y.<Z>](https://PATH_TO_REPO/compare/vX.Y.Z...hotfix\/vX.Y.<Z>)
  ## [Unreleased](https://PATH_TO_REPO/compare/vX.Y.Z...develop)

  NEW CHANGE_LOG:
  ## [X.Y.<Z>](https://PATH_TO_REPO/compare/vX.Y.Z...vX.Y.<Z>) - <yyy-mm-dd>
  ## [Unreleased](https://PATH_TO_REPO/compare/vX.Y.<Z>...develop)

  COMMIT:
  chore(*): finalize 'hotfix/vX.Y.<Z>'
  ```

- [ ] Merge `hotfix/vX.Y.<Z>` into `master`

  ```text
  COMMIT:
  Merge branch 'hotfix/vX.Y.<Z>' into master
  ```

  ```text
  TAG:
  vX.Y.<Z>
  ```

- [ ] Merge `hotfix/vX.Y.<Z>` into `develop`

  ```text
  COMMIT:
  Merge tag 'vX.Y.<Z>' into develop
  ```

- [ ] Merge `hotfix/vX.Y.<Z>` into `release` (if any)

  ```text
  COMMIT:
  Merge tag 'vX.Y.<Z>' into release/v<X>.<Y>.0
  ```

- [ ] Delete branch `hotfix/vX.Y.<Z>`

### Feature

A feature branch is used for developping a new feature (this should not be done on `develop` which is meant to be a collector to merge into). Name these branches `feature/<name>` where _\<name>_ should be short, yet unique within a project and descriptive enough for every developper to easily figure out what it is about.

> **Note.** _Unlike hotfixes and realeases that trigger major changes in the Changelog, features typically add only one line to the current `[Unreleased]` block upon termination. Would it seem justified for a feature to own its own Changelog block(s), then that feature is probably worth be promoted a project by itself._

#### (I) Start developping a new feature

- [ ] Create branch `feature/<name>` from `develop`

#### (II) Work out the new feature

- [ ] Commit changes as described in [Committing changes](#committing-changes)

&nbsp;&nbsp;&#9755;&nbsp;&nbsp;Avoid continous integration into other branches

#### (III) Terminate the new feature

- [ ] Merge `feature/<name>` into `develop`

  ```text
  COMMIT:
  Merge branch 'feature/<name>' into develop
  ```

- [ ] Changelog: on `develop`, add the _new feature_ to `[Unreleased]` block

  ```text
  CHANGE_LOG:
  ## [Unreleased](https://PATH_TO_REPO/compare/vX.Y.Z...develop)
  ### Added
  - Feature <name> which ...

  COMMIT:
  Update CHANGE_LOG with feature <nane> ...
  ```

- [ ] Delete branch `feature/<name>`

### Release

A `release` branch temporarily hosts the project for final debug before it is released. Creating one sets the version number of the next release and freezes the features it will make available: the `[Unreleased]` section of the Changelog is assigned the next version's number and any new feature merged into the `develop` past this point feeds a new `[Unreleased]` section describing the changes to come in the release coming after the one that was just started.

Every `release` starts on a strictly private and unversioned branch named `release/vX.Y.0`. Its li fe cycle ends when `release/vX.Y.0` is merged into both `master` and `develop`.

#### (I) Start a new release

- [ ] Branch `develop` to create `release/v<X>.<Y>.0`

- [ ] Changelog: initialize the release's block

  ```text
  CHANGE_LOG:
  ## [release/v<X>.<Y>.0](https://.../releases/compare/vX.Y.Z...release\/v<X>.<Y>.0)

  COMMIT:
  chore(*): initialize 'release/v<X>.<Y>.0'
  ```

- [ ] Merge `release/v<X>.<Y>.0` into `develop`  
       &#9755;&nbsp;&nbsp;_resolve conflicts by keeping the incoming changes_

  ```text
    COMMIT:
    Merge branch 'release/v<X>.<Y>.0' into develop
    ```

- [ ] Changelog: on `develop` declare a next version is started

  ```text
  CHANGE_LOG:
  ## [Unreleased](https://.../compare/release\/<X>.<Y>...develop)

  COMMIT:
  chore(*): initialize 'next release' after 'release/v<X>.<Y>.0'
  ```

#### (II) Test and deebug the new release

- [ ] Continous integration into `develop` is recommended

- [ ] Commit changes as described in [Committing changes](#committing-changes)

- [ ] The Changelog should be left unchanged

  ```text
  COMMIT:
  Merge branch 'release/v<X>.<Y>.0' into develop
  ```

#### (III) Terminate the new release

- [ ] Changelog: Finalize `release/v<X>.<Y>.0`

  ```text
  OLD CHANGE_LOG:
  ## [release/v<X>.<Y>.0](https://.../releases/compare/vX.Y.Z...release\/v<X>.<Y>.0)

  NEW CHANGE_LOG:
  ## [<X>.<Y>.0](https://PATH_TO_REPO/compare/vX.Y.Z...v<X>.<Y>.0) - <yyyy-mm-dd>

  COMMIT:
  chore(*): finalize 'release/v<X>.<Y>.0'
  ```

- [ ] Merge `release/v<X>.<Y>.0` into `master`

  ```text
  COMMIT:
  Merge branch 'release/v<X>.<Y>.0'
  ```

  ```text
  TAG:
  v<X>.<Y>.0
  ```

- [ ] Merge `release/v<X>.<Y>.0` into `develop`

  ```text
  COMMIT:
  Merge tag 'v<X>.<Y>.0' into develop
  ```

- [ ] Delete branch `release/v<X>.<Y>.0`
