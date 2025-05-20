Make your entrypoint.sh file executable. Git provides a way to explicitly change the permission mode of a file so that it doesn’t get reset every time there is a clone/fork
```sh
git add entrypoint.sh
git update-index --chmod=+x entrypoint.sh
```

to check the permission mode of the file in the git index, run the following command.
```sh
git ls-files --stage entrypoint.sh
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
