# SFDX CLI Bugs

There are two identified issues introduced in version 7.156.0 of the sfdx-cli. Each issue does not exist when using version 7.155.1 or prior, meaning you can install a prior version of the CLI (7.155.1, for example) and not see the issue mentioned.

## REST Deploy Not Working

When using 7.156.0 or greater of the sfdx-cli, REST deploy is no longer working.

**Expected**

```bash
➜ SFDX_REST_DEPLOY=true sfdx force:source:push
*** Pushing v55.0 metadata with REST API v54.0 connection ***
```

**Actual**

```bash
➜ SFDX_REST_DEPLOY=true sfdx force:source:push
*** Pushing with SOAP API v55.0 ***
```

## `.forceignore` in Subdirectory Takes Precedence

Prior to version 7.156.0, if there was a `.forceignore` file in a subdirector of the project root where sfdx commands are run, it was ignored, and the one at the root was used.

After version 7.156.0, it appears that the `.forceigore` files in subdirectories take precedence, and the one at the root is ignore completely.

**Expected**

When pushing this project's source to the scratch org, nothing is pushed - because it is ignored at the project root's `.forceignore`.

**Actual**

The permission set is pushed to the scratch org.
