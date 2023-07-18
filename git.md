# STRV Git Guidelines

This document is focused on the following topics:

- [GitHub](#github)
- [Repositories](#repositories)
- [Naming Convention of Repositories](#naming-convention-of-repositories)
- [Teams](#teams)
- [Branches](#branches)
- [Committing and Pushing](#committing-and-pushing)
- [Commit Messages](#commit-messages)
- [Pull Requests](#pull-requests)
- [Code Reviews](#code-reviews)
- [Tags](#tags)
- [Backup and Archiving](#backup-and-archiving)

## GitHub

- We use GitHub for hosting Git repositories
- We require two-factor authentication

## Repositories

- Each project must have proper *.gitignore*, ignoring temporary files and binaries
- Each project must have a *README.md* file with instructions and other important notes about how to build it, run it, and test it

## Naming Convention of Repositories

- Use `lowercase`, `kebab-case` for repository names
- Naming formula for projects: `<project>-<platform>-<module>`
- Naming formula for templates and other internal repositories: `<platform>-<module>`
- The `<platform>` part is one of these: *android*, *ios*, *flutter*, *rn*, *unity*, *backend-go*, *backend-nodejs*, *frontend-react*, *ds*
- The `<module>` part is optional
- If the project name consists of multiple words, use dashes as a separator, e.g. `rich-uncles-flutter`
- If project has multiple versions, use *v1*, *v2* suffixes, e.g. `float-backend-go-api-v1`, `float-backend-go-api-v2`
- The same rules above apply to public repositories
- Examples of project repository names: `surge-android`, `surge-ios`, `surge-backend-nodejs-api`, `surge-frontend-react-admin`, `surge-ds-recommendation`
- Examples of internal repositories: `android-template`, `ios-snippets`, `backend-nodejs-academy-2022`, `frontend-react-authentication-services`, `ds-data-stack`

## Teams

- Each project should have a team at GitHub
- Each repository should be assigned to a team
- Developers should be assigned to teams rather than to specific repositories
- Use `PascalCase` for team names, e.g. `RichUncles`
- If you need to add a suffix, separate it with the dash symbol, e.g. `RichUncles-Admin`

## Branches

- Each project should have *master* and *dev* branches, use *dev* rather than *develop*
- The master branch should be kept stable at all times, it reflects code currently running on production
- Code in master and dev branches should always be buildable
- Use `lowercase`, `kebab-case` for branch names, e.g. `database-migration`
- Use `feature/` prefix for feature branches, e.g. `feature/password-reset`
- Use `fix/` prefix for bugfixes, e.g. `fix/time-zone`
- Use `refactor/` prefix for refactoring, e.g. `refactor/update-libraries`
- Always remove inactive branches
- We strongly recommend [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/) for bigger teams, optional for smaller teams

## Committing and Pushing

- Each commit should address 1 logical change
- Never commit temporary files, binaries or other compiled sources, etc.
- Never commit passwords or other sensitive data to a public repository
- When you make a private repository public, always consider recreating all secrets which might have ever been part of the Git history
- Use `git push --force` only on feature branches and when you are sure nobody from your team is working on that branch or has another branch based off of that branch
- Don't commit code with trailing whitespace
- Don't commit code without a new line at the end of the file ([POSIX standard](https://stackoverflow.com/questions/729692/why-should-text-files-end-with-a-newline))
- Make sure all tests and linter pass before pushing any code
- Follow the "leave the campground cleaner than you found it" rule for any code you commit

## Commit Messages

- You have two options to choose from

### Conventional Commits

- Simply follow the [`Conventional Commits`](https://www.conventionalcommits.org) strategy
- Following this convention allows other tools to extract meaningful data from your commits and in turn offer you:
    - Automatic semantic release versioning
    - Changelog generation
    - Clear visibility into breaking changes
- Conventional commits can be optionally enforced (linted) using [`commitlint`](https://commitlint.js.org) and [`@strv/commitlint-config`](https://github.com/strvcom/code-quality-tools/tree/master/packages/commitlint-config)

### General Commits Conventions

- Message should describe the changes in the code well
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use present tense, imperative mood in the subject line, e.g. `Add online indicator`, not ~~`Adds online indicator`~~, ~~`Added online indicator`~~
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how (i.e. describe why this feature exists in terms of business value rather than how you implemented it, unless the implementation itself is complex enough to warrant explaining to future developers)
- When merging into master, reference to pull request should be added
- When pushing into feature branch, no reference should be added, because pull request should contain reference to issue tracking system
- For example: `Fix NullPointerException in ProductListAdapter (#243)` is much better message than `fixed bug`; the latter is wrong, because it is in the past tense, in lowercase, not so descriptive, without reference to pull request
- Further reading about writing good commit messages can be found [here](https://chris.beams.io/posts/git-commit/)

## Pull Requests

- Before merging a feature branch into master, you should send a pull request and the pull request should be reviewed by another developer in the team
- Pull requests should be small, relevant to an issue, and properly described
- In order to provide all the necessary information to reviewer, fill in metadata on the pull request page in GitHub (Reviewers, Assignees, Projects, Linked issues), and use a template for pull request description.
- Another tips for good pull requests can be found [here](https://blog.ploeh.dk/2015/01/15/10-tips-for-better-pull-requests/)

### Template

```markdown
## Changes

Explain the changes you made. What does this implement or fix?

## Links

- [Issue #123](https://link.to/issue-tracking-system)

## Tested with

- Chrome 42 (macOS 42)
- iPhone 42 (iOS 42)
- Pixel 42 (Android 42)

## Checklist

- [ ] Lint and tests pass locally with my changes
- [ ] I've added tests that prove my feature works or that my fix is effective
- [ ] I've added necessary documentation
```

## Code Reviews

- Remember that good code review is more about communication than you being an know-all

### As reviewer

- In general, huge pull requests should be rejected
- Code reviews should be finished until one business day maximally
- Make sure that developer's code is well-designed, properly described, tested, documented and addresses the problem
- When writing your comments, be polite, explain your ideas, and balance giving explicit directions with just pointing out problems and letting the developer decide

### As developer

- Don't take reviewer's comments personally
- If a reviewer doesn't understand your code, it’s likely other future readers of the code won’t understand either; it means you should fix it

## Tags

- Follow [Semantic Versioning](https://semver.org/) for version tags, e.g. `1.4.2`
- Don't use "v" prefix in version tags, e.g. ~~`v1.4.2`~~
- Each release commit must be tagged with a version name

## Backup and Archiving

- Repositories from third party organizations should be backed up when project is finishing
- Repositories with last change older than 3 years should be backed up and archived
- Platform leaders are responsible for archiving repositories
- Use `git clone` command for the backup, e.g. `git clone git@github.com:strvcom/surge-android.git surge-android`
