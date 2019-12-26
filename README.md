# OpenShift Pruning

To apply:
```bash
oc project cluster-ops
oc process -f cronjob-prune-builds-deployments.yml -p KEEP_FAILED=3 -p KEEP_COMPLETE=25 -p PRUNE_TYPE=deployments | oc apply -f -
oc process -f cronjob-prune-builds-deployments.yml -p KEEP_FAILED=3 -p KEEP_COMPLETE=25 -p PRUNE_TYPE=builds | oc apply -f -
oc process -f cronjob-prune-images.yml -p IMAGE_PRUNE_KEEP_TAG_REVISIONS=25 | oc apply -f -
```
