Android Kernel Build action tests
=========

> [!NOTE]
> that this is not strictly a test, it is just a yaml-lint to check if each yml file is legitimate.

## How to use
First, you must install a TypeScript runtime(such as nodejs or bun).

Second, run `npm install` in tests directory if using nodejs.

Finally, run `npm run check` or `npx ts-node index.ts` or `bun run index.ts` in tests directory.

Such as:

```bash
user@localhost ~/k/tests (main)> npm run check
> kernel_build_action_yaml_eheck@0.0.3 check
> npx ts-node index.ts

Starting check...
Android Kernel Build Action YAML Checker v0.0.3

Checking ../action.yml ... [OK]     
Checking ../.github/workflows/check.yml ... [OK]     
Checking ../.github/workflows/build.yml ... [OK]     
Checking ../.github/workflows/main.yml ... [OK]
Checking ../.github/ISSUE_TEMPLATE/bug-report.yml ... [OK]     
Checking ../.github/ISSUE_TEMPLATE/config.yml ... [OK]     
Checking ../.github/dependabot.yml ... [OK]     

All YAML files checked successful,Total duration: 15ms
```
While breaking changes cause failed checking:
```bash
user@localhost ~/k/tests (main)> npm run check
> kernel_build_action_yaml_eheck@0.0.3 check
> npx ts-node index.ts

Starting check...
Android Kernel Build Action YAML Checker v0.0.3

Checking ../action.yml ... [ERROR]
Checking YAML file ../action.yml Unsuccessful.
Error: YAMLException: bad indentation of a mapping entry (257:9)

 254 |              test -d kernel/${{ inputs. ...
 255 |              test -d kernel/${{ inputs. ...
 256 |              echo "::endgroup::"
 257 |         fi
---------------^
 258 |
 259 |          cd kernel/${{ inputs.kernel-dir }}

YAML file check failed. Exiting ...
```

## Clean
run `npm clean` or `bun run clean.ts` to clean test directory
