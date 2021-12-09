# LitmusChaos Jenkins Template

- It is a CI template to run litmus experiment in jenkins pipelines stage.

- This template provides a way to perform a chaos experiments on the Kubernetes environment. It contains Litmus Chaos experiments to run the chaos and find a weakness in the system.

## Pre-requisites

- Use [Kubernetes Puglin](https://plugins.jenkins.io/kubernetes/) and [Kubernetes Contineous Deploy Plugin](https://plugins.jenkins.io/kubernetes-cd/)
- Kubernetes 1.17 or later

Notice The `jnlp` container in [Jenkinsfile](https://github.com/uditgaurav/jenkins-template/blob/5d01d58d0186d3b91c3b93ea49e0eee6ed5f70f2/Jenkinsfile#L10) is the default execution container. you can find the complete more details [here](https://github.com/jflowers/spring-petclinic/blob/blog-jenkins-agents-through-aggregation/Jenkinsfile).

## Execution Details

- The [pod-template](https://github.com/uditgaurav/jenkins-template/blob/master/pod-delete.yaml) used here is using `litmuschaos/chaos-ci-lib` image from [chaos-ci-lib](https://github.com/litmuschaos/chaos-ci-lib) repository which is a central point for all chaos execution.
- We can tune the ENVs in the template for set the certain paramerters like Application Details ( like name,namespace and kind), Chaos Details (like Chaos Duration, Chaos Interval etc ...)

## Create new template

- To create and use a new template we just need to update the `EXPERIMENT_NAME` with the [experiment name](https://github.com/litmuschaos/chaos-ci-lib/tree/master/experiments) supported in chaos-ci-lib. For Example to use container kill we can use:

```yaml
metadata:
  name: container-kill
  labels:
    experiment: container-kill
spec:
  serviceAccountName: litmus-jenkins-sa
  containers:
  - name: jnlp
    image: litmuschaos/chaos-ci-lib:v0.4.0
    imagePullPolicy: Always
    tty: true
    command: ["/bin/bash"]
    args:
    - -c 
    - ./experiment_entrypoint.sh
    env:
    - name: INSTALL_LITMUS
      value: "true"
    - name: EXPERIMENT_NAME
      value: "container-kill"
    - name: UNINSTALL_LITMUS
      value: "true
```

