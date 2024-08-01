# Udacity Git Commit Message Style Guide

A commit messages consists of three distinct parts separated by a blank line:

```txt
type: subject with 50 characters or less

body is optional and it has 72 characters per line -->

footer is optional
```

The first line is the subject. This should be a short description of what changed. Nothing like “fixed it” or “did something,” these need to be clear and informative, and try to avoid profanity. The subject should be 50 characters or less, with the first letter capitalized, and end without a period.

The type is contained within the title and can be one of these types:

- _feat_: a new feature
- _fix_: a bug fix
- _docs_: changes to documentation
- _style_: formatting, missing semi colons, etc; no code change
- _refactor_: refactoring production code
- _test_: adding tests, refactoring test; no production code change
- _trivial_: updating build tasks, package manager configs, etc; no production code change

The body is next, this is where you give a more detailed description of why you made the change. The body should typically have around 72 characters per line. This is to ensure that the message fits into a terminal window when using git on the command line. You’ll also need to make sure there is a blank line between the subject line and the body. You can also add bullet points, using asterisks or dashes, when you need to make a list. Use the body to explain the what and why of a commit, not the how.

Some commits don’t require a body in the message. If you fix a typo for example, it’s okay to only have a subject line.

You can also include a footer, typically this will be used to indicate which issues or bugs the commit addresses.

**Example**:

```txt
feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```
