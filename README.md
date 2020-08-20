# circleci-orbs

A repository for [orbs](https://circleci.com/orbs/) managed by Avvo for using in CircleCI.

**This is a public repository. See "Considerations about security" below.**

## Getting started

1. Familiarize yourself with [orbs from a developer perspective](https://circleci.com/docs/2.0/orb-intro/).

2. Get access to the Avvo Github organization.

3. Install the [CircleCI local CLI](https://circleci.com/docs/2.0/local-cli/) and run `circleci setup`

We've already run this command, **so you don't need to**: `circleci namespace create avvo github avvo`

## Creating a new orb

1. Create a new orb on CircleCI:

```
circleci orb create avvo/my-new-orb
```

2. Cut a new branch of this repo, and in it author a new orb in a file called `my-new-orb.yaml`. Validate it like this:

```
circleci orb validate my-new-orb.yaml
```

3. Assuming you've got no errors, publish a first version of your orb to CircleCI:

```
circleci orb publish my-new-orb.yaml avvo/my-new-orb@dev:initial
```

4. Write some CircleCI configs to test out your new orb on CircleCI. Keep running `circleci orb publish my-new-orb.yaml avvo/my-new-orb@dev:initial` while you iterate. When you're happy with your changes, do the following:

* Add your orb to your branch
* Push to Github
* Open a PR
* Go through the typical PR review and merge process

5. Once your PR is merged to master, checkout master in your local and run

```
circleci orb publish promote avvo/my-new-orb@dev:initial patch
```

This will promote your `dev:initial` version to the next available patch level.

## Editing existing orbs

This is much the same as creating a new orb, but you can skip the `circleci orb create` step. Also, you'll probably use a different tag than `dev:initial` because, well, it's not the initial development. Be creative. I believe in you.

## Considerations about security

CircleCI orbs are public, which is why this repo is public. *Don't commit code here that exposes Avvo secrets.*

If your code requires sensitive data such as a Github or package repository access credential, implement the access to that data using environment variables in your orb code. You can then configure the environment variables to passed into your CircleCI build configuration via [contexts](https://circleci.com/docs/2.0/contexts/) or [project-level environment variables](https://circleci.com/docs/2.0/env-vars/#setting-an-environment-variable-in-a-project).

See [the CircleCI docs on environment variables](https://circleci.com/docs/2.0/env-vars/) to learn more about how environment variables are used and managed in CircleCI.
