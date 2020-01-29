# CircleCI: Continuous Integration and Delivery

When we work on software, changes get integrated continuously, and there comes the word `Continuous Integration`.

CircleCI ensures that when a PR is raised with code changes, it does not break our tests.

This repo is dedicated to setting up circleci and fixing issues if any arises.

# Issues and their solutions.

1. Your ruby version is `x` but your gemfile specified `y`.
  To resolve this issue, just make sure that your docker image ruby version is same as the version of ruby specified by your     gemfile (y).
  
  ```yml
  version: 2
  jobs:
  build:
    parallelism: 6
    docker:
      # specify the version you desire here
       - image: circleci/ruby:y-node-browsers
  ```

2. Could not find bundler (x) required by your gemfile.
  To resolve this issue, just make sure that right version of bundler is installed before starting to build the circleci test.   Here (x) is the bundler version with which your gemfile is bundled. Add the following line in config.yml file under steps `- run: gem install bundler:x`.
  
  ```yml
  steps:
    - checkout
    - run: gem install bundler:x
  ```
