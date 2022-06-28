# policy controller - custom policy demo #

# Problem - limit number of max instances for hpa #

## create contraint template ##

kubectl apply -f k8shpalimit-template.yaml

## create constraint ##

kubectl apply -f hpa-violation-constraint.yaml

## view constraints for violation ##

kubectl get k8shpalimit.constraints.gatekeeper.sh/hpa-violation -o yaml

## create the hpa ##

kubectl apply -f hpa.yaml

## view the constraint (there should be at least 1 violation at this time) ##

kubectl get k8shpalimit.constraints.gatekeeper.sh/hpa-violation -o yaml
