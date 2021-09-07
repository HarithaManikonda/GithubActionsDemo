GitHub Actions help you automate tasks within your software development life cycle.
GitHub Actions are event-driven.For example, every time someone creates a pull request for a repository, you can automatically run a command that executes a software testing script.

![Screen Shot 2021-09-06 at 7 52 46 PM](https://user-images.githubusercontent.com/87215340/132276882-3fd4096b-da4f-4fff-8c30-9d1b3714d091.png)



1. Workflows
2. Events
3. Jobs
4. Runners
5. Steps
6. Actions

## Workflows

The workflow is an automated procedure that you add to your repository. Workflows are made up of one or more jobs and can be scheduled or triggered by an event. The workflow can be used to build, test, package, release, or deploy a project on GitHub.

## Events

An event is a specific activity that triggers a workflow. For example, activity can originate from GitHub when someone pushes a commit to a repository or when an issue or pull request is created.

## Jobs

A job is a set of steps that execute on the same runner. By default, a workflow with multiple jobs will run those jobs in parallel. You can also configure a workflow to run jobs sequentially

## Steps

A step is an individual task that can run commands in a job. A step can be either an action or a shell command

## Actions

Actions are standalone commands that are combined into steps to create a job. Actions are the smallest portable building block of a workflow. You can create your own actions, or use actions created by the GitHub community

## Runners

A runner is a server that has the GitHub Actions runner application installed. You can use a runner hosted by GitHub, or you can host your own. A runner listens for available jobs, runs one job at a time, and reports the progress, logs, and results back to GitHub



## Maven workflow template

GitHub provides a Maven workflow template that will work for most Maven-based Java projects. For more information, see the Maven workflow template.
To get started quickly, you can choose the preconfigured Maven template when you create a new workflow. 
You can also add this workflow manually by creating a new file in the .github/workflows directory of your repository.
YAML
```
name: Java CI


on: [push]


jobs:
  build:
    runs-on: ubuntu-latest


    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
      - name: Build with Maven
        run: mvn --batch-mode --update-snapshots verify
```
This workflow performs the following steps:

1. The checkout step downloads a copy of your repository on the runner.
2. The setup-java step configures the Java 11 JDK by Adoptium.
3. The "Build with Maven" step runs the Maven package target in non-interactive mode to ensure that your code builds, tests pass, and a package can be created.

## Running on a different operating system

The starter workflow template configures jobs to run on Linux, using the GitHub-hosted ubuntu-latest runners. You can change the runs-on key to run your jobs on a different operating system. For example, you can use the GitHub-hosted Windows runners.

```
runs-on: windows-latest
```
When a commit is made to the repo , github actions workflow job will be execute and we have ouput as below.

![Screen Shot 2021-09-06 at 7 55 38 PM](https://user-images.githubusercontent.com/87215340/132277275-bcc20669-8313-4158-92cc-cb142f8f9705.png)
![Screen Shot 2021-09-06 at 7 55 58 PM](https://user-images.githubusercontent.com/87215340/132277267-ae011f54-5b22-4b4d-8465-52ee7b8880c3.png)

## References
https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions
