# azure-pipeline-templates

Templates for [Azure Pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/)

## [`rust.yml`](rust.yml)

```yaml
trigger: ["master"]
pr: ["master"]

resources:
  repositories:
    - repository: templates
      type: github
      name: alecmocatta/azure-pipeline-templates

jobs:
- template: rust.yml@templates
  parameters:
    default:
      rust_toolchain: nightly
      rust_lint_toolchain: nightly-2019-07-15
      rust_flags: ''
      rust_features: ''
      rust_target_check: ''
      rust_target_build: ''
      rust_target_run: ''
    matrix:
      windows:
        imageName: 'vs2017-win2016'
        rust_target_run: 'x86_64-pc-windows-msvc x86_64-pc-windows-gnu i686-pc-windows-msvc i686-pc-windows-gnu'
      mac:
        imageName: 'macos-10.13'
        rust_target_run: 'x86_64-apple-darwin i686-apple-darwin'
      linux:
        imageName: 'ubuntu-16.04'
        rust_target_run: 'x86_64-unknown-linux-gnu i686-unknown-linux-gnu x86_64-unknown-linux-musl i686-unknown-linux-musl'
```

## License
Licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE.txt](LICENSE-APACHE.txt) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT.txt](LICENSE-MIT.txt) or http://opensource.org/licenses/MIT)

at your option.

Unless you explicitly state otherwise, any contribution intentionally submitted for inclusion in the work by you, as defined in the Apache-2.0 license, shall be dual licensed as above, without any additional terms or conditions.
