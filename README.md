# Happy Prime Travis Deploys

This deployment configuration is used as a base at Happy Prime for managing deployments from Travis.

Projects will be deployed to the `deploy` user's home directory under a path built from the repository slug and branch name.

## Configuration

This repository contains an encrypted private key (`hp_deploy_rsa.enc`) attached to a `deploy` user on a server. If this repository is forked as part of another project, the key may need to be replaced and the environment variable in `travis.yml` for `HP_KEY_FILE` should be changed accordingly.

Use the following to generate an encrypted key file for a repository:

```
ssh-keygen -t rsa -b 4096 -C 'build@travis-ci.org' -f ./deploy_rsa
travis encrypt-file deploy_rsa
```

The `travis` command line client can be installed with `gem install travis`.

The build directory that should be synced from Travis can be configured with the global environment variable `HP_BUILD_DIR`.
