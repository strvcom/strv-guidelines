STRV Git Guidelines
===================

GitHub
------

- We use GitHub for hosting Git repositories
- We require two-factor authentication

Repositories
------------

- Use `lowercase`, `kebab-case` for repository names
- Repository name should consist of three parts: `<project>-<platform>-<module>`, the `<module>` part is optional and the `<platform>` part is one of these: *android*, *ios*, *backend*, *frontend*, *rn*, *unity*
- Examples of repository names: `surge-android`, `surge-ios`, `surge-backend-api`, `surge-frontend-admin`, `surge-rn`
- If project name consists of multiple words, use dashes as a separator, e.g. `rich-uncles-frontend`
- If project has multiple versions, use *v1*, *v2* suffixes, e.g. `futupilot-backend-api-v1`, `futupilot-backend-api-v2`
- If API, web or RN are mixed in a single repository, use `js-monorepo` as a platform identifier, e.g. `ordr-js-monorepo`
- The same rules above apply to public repositories
- Each project must have proper *.gitignore*, ignoring temporary files and binaries 
- Each project must have a *README.md* file with instructions and other important notes about how to build it and run it

Teams
-----

- Each project should have a team at GitHub
- Each repository should be assigned to a team
- Developers should be assigned to teams rather than to specific repositories
- Use `PascalCase` for team names, e.g. `RichUncles`
- If you need to add a suffix, separate it with the dash symbol, e.g. `RichUncles-Admin`

Branches
--------

- Each project should have *master* and *dev* branches, use *dev* rather than *develop*
- The master branch should be kept stable at all times, it reflects code currently running on production
- Code in master and dev branches should always be buildable
- Use `lowercase`, `kebab-case` for branch names, e.g. `database-migration`
- Use `feature/` prefix for feature branches, e.g. `feature/password-reset`
- Use `fix/` prefix for bugfixes, e.g. `fix/time-zone`
- Use `refactor/` prefix for refactoring, e.g. `refactor/update-libraries`
- Always remove inactive branches
- We strongly recommend [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/) for bigger teams, optional for smaller teams

Pull Requests
-------------

- Developers in a team should send a pull request before merging a branch and the pull request should be reviewed by another developer in the team

Committing and Pushing
----------------------

- Each commit should address 1 logical change
- Never commit temporary files, binaries, etc.
- Never commit passwords or other sensitive data to a public repository
- Never use `git push --force`
- Don't commit code with trailing whitespaces
- Don't commit code without a new line at the end of the file ([POSIX standard](https://stackoverflow.com/questions/729692/why-should-text-files-end-with-a-newline))
- Make sure all tests and linter pass before pushing any code
- Follow the "leave the campground cleaner than you found it" rule for any code you commit

Commit Messages
---------------

- Message should describe the changes well in the code
- Follow [this commit message convention](https://chris.beams.io/posts/git-commit/)
- Separate subject from body with a blank line
- Limit the subject line to 50 characters
- Capitalize the subject line
- Do not end the subject line with a period
- Use present tense, imperative mood in the subject line, e.g. `Add online indicator`, not ~~`Adds online indicator`~~, ~~`Added online indicator`~~
- Wrap the body at 72 characters
- Use the body to explain what and why vs. how
- If you use an issue tracker, put references to them at the end of the message
- For example: "Fix NullPointerException in ProductListAdapter" is a much better message than "fixed bug", the latter is wrong, because it is in past tense, in lowercase and not so descriptive

Tags
----

- Follow [Semantic Versioning](https://semver.org/) for version tags, e.g. `1.4.2`
- Don't use "v" prefix in version tags, e.g. ~~`v1.4.2`~~
- Each release commit must be tagged with a version name

Backup and Archiving
--------------------

- Repositories from third party organizations should be backed up when project is finishing
- Repositories with last change older than 3 years should be backed up and archived
- Platform leaders are responsible for archiving repositories
- Use `git clone` command for the backup, e.g. `git clone git@github.com:strvcom/surge-android.git surge-android`

Pull Request Template
---------------------

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
