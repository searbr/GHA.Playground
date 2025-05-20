# Notes
Make your entrypoint.sh file executable. Git provides a way to explicitly change the permission mode of a file so that it doesn’t get reset every time there is a clone/fork
```sh
git add entrypoint.sh
git update-index --chmod=+x entrypoint.sh
```

to check the permission mode of the file in the git index, run the following command.
```sh
git ls-files --stage entrypoint.sh
```

## Accessing files created by a container action 
When a container action runs, it will automatically map the default working directory (GITHUB_WORKSPACE) on the runner with the /github/workspace directory on the container. Any files added to this directory on the container will be available to any subsequent steps in the same job. For example, if you have a container action that builds your project, and you would like to upload the build output as an artifact, you can use the following steps.

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      # Output build artifacts to /github/workspace on the container.
      - name: Containerized Build
        uses: ./.github/actions/my-container-action

      - name: Upload Build Artifacts
        uses: actions/upload-artifact@v4
        with:
          name: workspace_artifacts
          path: ${{ github.workspace }}
```

# Hello world docker action

This action prints "Hello World" or "Hello" + the name of a person to greet to the log.

## Inputs

## `who-to-greet`

**Required** The name of the person to greet. Default `"World"`.

## Outputs

## `time`

The time we greeted you.

## Example usage

uses: actions/hello-world-docker-action@v2
with:
  who-to-greet: 'Mona the Octocat'
