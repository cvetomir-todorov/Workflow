# Introduction

Git repo layout is important in order to know where certain files are located.

```bash
bin/
cicd/
deploy/
  docker/
  minikube/
  aws/
docs/
  diagrams/
  images/
lib/
package/
  ceco-chat/
  efk/
source/
  CecoChat/
  CecoChat.HistoryConsumer/
  CecoChat.Messaging/
  CecoChat.Testing/
  cecochat-all.sln
  cecochat-messaging.sln
  cecochat-history-consumer.sln
.gitignore
CHANGELOG
LICENSE
README.md
```

* `bin/` - contains temp files created during CICD pipeline (dll, pdb, nupkg etc.)
  - the dir should obviously be git ignored
* `cicd/` - contains files related to the CICD pipeline (GitLab/GitHub files, custom scripts etc.)
* `deploy/` - contains files related to deployment (docker, kubernetes, etc.)
* `docs/` - contains the documentation
* `lib/`
  - should be **AVOIDED**
  - NuGet packages should be defined, if needed
  - adding big files increases size of repo making `git clone` slow
* `package/` - contains Dockerfiles, nuspec files
* `source/` - contains the source code
  - includes both production and test projects
  - includes one or more solutions
* `.gitignore`
* `CHANGELOG` - contains a list of changes by version and date
* `LICENSE` - contains the license of the repo
* `README.md` - contains a repo intro and links to the documentation
