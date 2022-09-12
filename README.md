# kubectl-pick-job
Pick one time job from CronJob list interactively.


Install
-----------

Just copy `kubectl-pick-job` file under any `$PATH` directory. `chmod +x` is also needed.
kubectl will find it as a plugin.

kubectl-pick-job requires bash >= 4.0.  
Most Linux distros have them. MacOS is shipped with older bash.


Usage
-----------

Just run `kubectl pick job`, and you'll see the CronJob list.  
Single job is created after selecting one.

```bash
$ kubectl pick job -h

kubectl pick job version v1.0.0
  Usage:    kubectl pick job [options] [cronjob name>]
  Options:
            -n <namespace>   Specify namespace
            -h               Show this usage
```


### Delete Job

Set `ttlSecondsAfterFinished: <seconds>` to `spec.jobTemplate.spec` in each CronJob manifest.

It clears up completed jobs automatically.

You can refer to [JobSpec](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/job-v1/#JobSpec) for further infomation.

Without `ttlSecondsAfterFinished`, you need to delete previous jobs manually with `kubectl delete`.  
This plugin does nothing after job creation.


For Tekton
-----------

As a tekton-pipelines flavor, there is [tkn-runner](https://github.com/chumaltd/tkn-runner).  
You can construct more complex CI tasks with tekton.
