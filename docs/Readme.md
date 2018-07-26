### Hosting helm charts via github

Helm charts repository is nothing but bunch of zip files served by a server.
Its mostly static data. Follow below steps at root directory, and get your
PR merged.

Following: https://docs.helm.sh/developing_charts/#hosting-chart-repositories

~~~sh
# First create zip files for charts
cd /path/to/cloned/repo/of/helm-charts
helm package dockup
helm package db-pool

# Now move generated packages to docs folder
mv dockup-*.tgz docs
mv db-pool-*.tgz docs

# Update index file in docs folder
cd docs
helm repo index --url=https://helm-charts.codemancers.github.io .
~~~


Now commit changes, open a PR and get it merged. Ensure that you change
version of charts before publishing.