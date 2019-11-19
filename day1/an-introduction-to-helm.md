An Introduction to Helm
-----------------------

Helm is a package manager for k8, came from Deis (like yum!).
Package management: tooling that enables someone who has no knowledge of an app to run it or use it.

### Is Helm trustworthy?
* Passed security audit report (from cure53)
* Longetivity (in dog years? since 2015)
    * CNCF sponsorship
    * bunch of maintainers and companies
* semver usage, great job
    * also use release candidates

### Digging in to Helm
* Can specifiy dependencies in chart
* values.yaml
    * all the settings for the chart
* templates
    * yaml templates, uses template language within go to tEmPlATe ThE FiLe
    * good to have the same chart in dev, uat, prod
* helpers
    * optional, sections of yaml that you want to repeat all over the place
* tests
    * helm test file, helm command will look at file and run service check to verify chart was installed

### More to Helm
* helm/hub on github
* helm hub runs monocular
    * can use monocular to run our own chart repo
    * But use ChartMuseum instead!
        * is fancy
* helm/chart-testing

### Beyond Helm
* flux, drone, airship
* helmfile: config management system that sits ontop of helm
* Cloud Native Experiments
    * Ability to use OCI (open container initiative) repositories to store helm charts

slack: #helm-users, #helm-dev, #charts
Developer call - thursday at 9:30am PT (posted on youtube)