% Managing AWS through Ansible and CI
% Will Thames
% 27 April 2017

---

# Contents

* What is CI
* Using Ansible to build CI on AWS
* Using Ansible for CI

---

# Resources

* Repository
* Slides
* Code

---

# What is CI

> Continuous integration is any system that
> runs a test suite every time code is committed.

> The main purpose of CI is to provide confidence
> that what will go into production has been suitably
> tested

---

# Typical features of CI

* Notice when code is committed
* Run `build` job on code change
* Run `unit test` job when build is complete
* Run `deploy` job if build tests pass
* Run `integration test` job against deployment
* Run `promote` job if `integration test` passes in test environment
* Configure jobs to run only for certain
  criteria - named branches or branch patterns,
  new tags, etc.

---

# Modern CI frameworks

Creating CI jobs has historically been quite point and click,
meaning that it was difficult to automate new jobs.

Services such as Travis, Circle, Shippable etc. allow CI tasks to be
specified in a configuration file alongside the code.

More recently, Jenkins now allows the configuration of CI to be
in code, through the Jenkinsfile. Gitlab CI also provides
gitlab-ci.yml as a similar mechanism.

Atlassian have been thinking about it for Bamboo for
three years [BAM-15087](https://jira.atlassian.com/browse/BAM-15087)

---

# AWS solutions for CI

* Run unit tests in containers on ECS
* Use AWS instances as a clean deployment target for testing
* Convert deployment result into an AMI for promotion
* Run tests against Lambda functions before making live
* Use Code Commit, Code Build and/or Code Pipeline as
  components of a CI platform

# Building CI using Ansible

[Demo]

---

# Running CI tests with Ansible

[Demo]
