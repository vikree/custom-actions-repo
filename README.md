# custom-actions-repo
Explanation:
Custom Actions:

Build Action: Located at example/custom-actions-repo/steps/build_action.yml in the external repository.
Push Action: Located at example/custom-actions-repo/steps/push_action.yml in the external repository.
Generic CI Workflow Template (generic-CI.yaml):

Located at example/custom-actions-repo/template/generic-CI.yaml.
Uses the workflow_call event to define inputs (tags and build-args).
Calls the build and push custom actions using the correct paths and passes the inputs.
Application's Main Workflow (main.yaml):

Located at .github/workflows/main.yaml in your application repository.
Calls the generic CI workflow template from the external repository using the uses keyword.
Passes the required inputs (tags and build-args) to the generic workflow.
Example:
If the custom actions and the generic CI workflow are located in a repository named custom-actions-repo under the owner example, and you want to use the main branch, you would reference them as follows:

      jobs:
        call-generic-ci:
          uses: example/custom-actions-repo/template/generic-CI.yaml@main
          with:
            tags: user/containerRepository:latest
            build-args: CUSTOM_BUILD_ARG=value
