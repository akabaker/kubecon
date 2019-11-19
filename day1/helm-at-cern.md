Managing Helm Deployments with GitOPS at CERN
---------------------------------------------

Puppet -> Helm

### Charts repo
* Chartmuseum
* internal repo, and mirror charts (upstream mirror)
* Trigger by gitlab CI

Use 'Umbrella charts'
* nginx with mysql, create chart to deploy both together

### Managing secrets
* treat secrets as config
* encrypt secrets in values file
* helm-secrets does this
* helm-barbican

### Flux and GitOps
docker push -> registry
git push -> meta chart <- git pull [flux cd -> helm release <-> helm operator]

ricardo.rocha@cern.ch