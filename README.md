# circleci-orbs

A repository for [orbs](https://circleci.com/orbs/) managed by Avvo for using in CircleCI.

## Getting started

Familiarize yourself with [orbs from a developer perspective](https://circleci.com/docs/2.0/orb-intro/).

1. Get access to the Avvo Github organization.

2. Install the [CircleCI local CLI](https://circleci.com/docs/2.0/local-cli/) and run `circleci setup`

3. We've already run this command, **so you don't need to**: `circleci namespace create avvo github avvo`

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


