# OpenShift 4 Multi Cluster Failover

S2I configuration and pipelines for [OpenShift Jenkins]() to demonstrate multi-cluster failover of an application.

# Prepare OpenShift Clusters

```
# Set environment specific parameters
APP_PROJECT_A=app-a
APP_PROJECT_B=app-b
JENKINS_PROJECT=jenkins

# Configure OpenShift
oc new-project ${APP_PROJECT_A}
oc new-project ${APP_PROJECT_B}
oc new-project ${JENKINS_PROJECT}
oc new-app jenkins -n ${JENKINS_PROJECT}
oc policy add-role-to-user edit system:serviceaccount:${JENKINS_PROJECT}:jenkins -n ${APP_PROJECT_A}
oc policy add-role-to-user edit system:serviceaccount:${JENKINS_PROJECT}:jenkins -n ${APP_PROJECT_A}
```  