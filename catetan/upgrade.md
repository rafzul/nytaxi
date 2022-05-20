link Return to Table of Contents for more guides link

    Note, this page was written for the User-Community Airflow Helm Chart

Upgrade Guide
Step 1 - Prepare your Changes

This guide is applicable in the following situations:

    upgrading to newer versions of the chart
    applying changes made to your custom-values.yaml file

Step 2 - Apply your Changes

## pull updates from the helm repository
helm repo update

## set the release-name & namespace (must be same as previously installed)
export AIRFLOW_NAME="airflow-cluster"
export AIRFLOW_NAMESPACE="airflow-cluster"

## apply any changed `custom-values.yaml` AND upgrade the chart to version `8.X.X`
helm upgrade \
  "$AIRFLOW_NAME" \
  airflow-stable/airflow \
  --namespace "$AIRFLOW_NAMESPACE" \
  --version "8.X.X" \
  --values ./custom-values.yaml

    red_square Warning red_square

    Always pin the --version so you don't unexpectedly update chart versions!

    red_square Warning red_square

    Before upgrading chart versions, always consult CHANGELOG.md!

    blue_square Tip blue_square

    Watch 👀 on GitHub to be notified about new chart versions, click "watch" → "custom" → "releases".
