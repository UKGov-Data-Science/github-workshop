# R & GitHub Best Practices
Gábor Csárdi  

# Continuous Integration

## Concept

## Travis

## Set it up for an R package

# Test coverage

## Concept

## Set it up on Travis

# Best Practices

# What to include in the package

## Tests

## README.md file

## NEWS.md file

## Version numbers, semantic versioning

## Keep repos clean, use a .gitignore file

## Collaborate with yourself

## Use cross-references in comments, issues, commit messages

* Close an issue with a commit message
* Value other people's time:
  - No +1 comments (although now this is better)
  - No thank you comments!
  - No unneeded references to commits and issues
  - Do not submit large pull requests without asking the owner(s)
    if they want them
  - Comply with the repo standards. Really, do what the owner says.
    (They will have to manage this code in the future.)
  - Contributions as the owner sees them: more shitty code to maintain
  - As the contributor sees them: I am adding this cool feature
  - Don't be upset if
    o your issue is not answered
    o your PR is ignored
	o you are told to change your PR
	o your PR is rejected
  - It is OK to make a friendly reminder comment, or two
	(usually not OK, to email privately!)

## RSS/Atom feeds for commits

## Gists

* Public vs secret

## GitHub API

* Manipulating GitHub using gaborcsardi/gh
* Get a GitHub token
* GITHUB_PAT environment variable

## Not just code

* Why git & GitHub is great for R Markdown
* Presentations
* Scientific articles (not in word)
* Anything that is text, really: Awesome R

## Pain points

* If something goes wrong, it will be hard to fix it.
  Just don't tinker with the history. If you do, always
  make backups first.
* No code review tools with R support
* No multi-platform continuous integration support
* R package GitHub repo is also for distribution:
  auto-generated files are in the repository,
  diffs are bloated.
* Price

## Additional material

* Software carpentry
* GitHub help pages
* Hadley Wickham's R packages book