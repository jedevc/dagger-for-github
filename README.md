# GitHub action to run Dagger

## Usage Examples

### `dagger call` (default)

```yaml
- name: Hello
  uses: dagger/dagger-for-github@v6
  with:
    verb: call
    module: github.com/shykes/daggerverse/hello
    args: hello --greeting Hola --name Jeremy
    cloud-token: ${{ secrets.DAGGER_CLOUD_TOKEN }}
```

### `dagger run`

```yaml
- name: Integration Test
  uses: dagger/dagger-for-github@v6
  with:
    workdir: db-service
    verb: run
    args: node build.js
    cloud-token: ${{ secrets.DAGGER_CLOUD_TOKEN }}
    version: "0.13.3"
```

### Staying in sync with the `latest` version

By setting the version to `latest`, this action will install the latest version of Dagger.

### All `with:` input parameter options

| Key            | Description                                                 | Required | Default            |
| -------------- | ----------------------------------------------------------- | -------- | ------------------ |
| `version`      | Dagger Version                                              | false    | '0.13.3'           |
| `dagger-flags` | Dagger CLI Flags                                            | false    | '--progress plain' |
| `verb`         | CLI verb (call, run, download, up, functions, shell, query) | false    | 'call'             |
| `workdir`      | The working directory in which to run the Dagger CLI        | false    | '.'                |
| `cloud-token`  | Dagger Cloud Token                                          | false    | ''                 |
| `module`       | Dagger module to call. Local or Git                         | false    | ''                 |
| `args`         | Arguments to pass to CLI                                    | false    | ''                 |
| `engine-stop`  | Whether to stop the Dagger Engine after this run            | false    | 'true'             |
