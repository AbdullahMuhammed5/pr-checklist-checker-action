# pr-checklist-checker-action

This is a Github action package that checks if all tasks in the pull request are completed. 

## Benefits

- Standardization: Ensures all developers follow the same review and documentation process, improving consistency and reducing confusion.
- Simplified reviews: Reviewers can focus on deeper technical aspects knowing basic checks are already passed.
- Documentation completeness: Guarantees that PR documentation is filled out and provides necessary information.
- Accountability: Encourages developers to take ownership of their code and documentation.

## How it works 

It simply looks for any checkbox in the pull request template body and then make sure that all of them are checked and completed. 

If some of the required checkbox is not checked yet, the action job will fail.

if you need to ignore some checkbox or make them optional, you can simply wrap them inside a block. (Check the example below)


## Example

``` md
## Issue Type
<!-- ignore-task-list-start -->
- [ ] Bug
- [ ] Document
- [ ] Enhancement
<!-- ignore-task-list-end -->

## Checklist
- [ ] My code follows the style guidelines of this project
- [ ] I have performed a self-review of my own code
- [ ] **I have added tests that prove my fix is effective or that my feature works**
- [ ] **New and existing unit tests pass locally with my changes**
- [ ] I have commented my code, particularly in hard-to-understand areas.
```

## Usage

### Create a workflow

In your `.github/workflows` directory create a new yml file with the below code

``` yml
name: 'PR TaskList Completed Checker'
on: 
  pull_request:
    types: [opened, edited, reopened, synchronize]

jobs:
  task-check:
    runs-on: ubuntu-latest
    name: A job to test task list completed 
    steps:
      - name: Run job
      - uses: abdullahmuhammed5/pr-checklist-checker-action@1.0.0
```