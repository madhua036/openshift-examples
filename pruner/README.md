```sh
apiVersion: batch/v2alpha1
kind: CronJob
metadata:
  name: prune-images
spec:
  schedule: 0 */1 * * ?
  jobTemplate:
    metadata:
      labels:
        job: prune-images
    spec:
      template:
        spec:
          containers:
          - name: prune-images
            image: openshift/origin:latest
            args: [ "admin", "prune", "images", "--confirm"]
          restartPolicy: OnFailure
```          
