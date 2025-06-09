1. To get all the pods details in json config format. 

`kubectl get pods -o json`

2. To get specific information - string filter - examples

`kubectl get pods -o jsonpath='{ .apiVersion }{"\n"}'`

3. To get specific information - from list attribute - examples

`kubectl get pods -o jsonpath='{ .items[*].spec.containers[0].imagePullPolicy }{"\n"}'`

4. Combine two different information.

`kubectl get pods -o jsonpath='{.items[0].spec.containers[0].name}{"\t"}{.items[0].spec.containers[0].imagePullPolicy}{"\n"}'`

5. Iterate through loop - Get Pod name & IP by iterating through items.

 `kubectl get pods -o jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.podIP}{"\n"}{end}{"\n"}'`

6. Add custom columns

`kubectl get nodes -o custom-columns=NODE:.metadata.name`

7. Sort by attribute

`kubectl get nodes --sort-by=.metadata.name`

