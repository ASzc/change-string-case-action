# Change String Case GitHub Action

This action accepts any string, and outputs three different versions of that string:

- lowercase (`XyZzY` -> `xyzzy`)
- uppercase (`XyZzY` -> `XYZZY`)
- capitalized (`Xyzzy` -> `Xyzzy`)

You can access the outputted strings through the job outputs context. See docs [here](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#jobsjobs_idoutputs), or the Example Usage section below.

## Inputs

### `string`

**Required** The string you want manipulated

## Outputs

### `lowercase`

`inputStr.toLowerCase()`

Example: `XyZzY` -> `xyzzy`

### `uppercase`

`inputStr.toUpperCase()`

Example: `XyZzY` -> `XYZZY`

### `capitalized`

`inputStr.charAt(0).toUpperCase() + inputStr.slice(1)`

Example: `XyZzY` -> `Xyzzy`

## Example Usage

```yaml
name: SomeWorkflow
on: [push]
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - id: string
        uses: ASzc/change-string-case-action@v1
        with:
          string: XyZzY
      - id: step2
        run: echo ${{ steps.string.outputs.lowercase }}
```
