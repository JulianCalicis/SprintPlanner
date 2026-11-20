| branch name     | base commit | special rules                                        |
| --------------- | ----------- | ---------------------------------------------------- |
| main            | root-commit | accepts PR from dev only                             |
| dev             | root-commit | merge squash to main, accepts PR from dev-<features> |
| dev-\<feature>  | dev         | branch from dev, rebase on dev, merge --no-ff to dev |
| fix-\<fix-name> | main        | branch from main, merge to main, cherry-pick to dev  |