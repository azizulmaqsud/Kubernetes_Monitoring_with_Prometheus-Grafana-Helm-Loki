Kubernetes Monitoring with Prometheus Grafana Helm Loki

## Install kube-prometheus-stack
- create a monitoring namespace 
- add prometheus-community repo
`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
`helm repo update prometheus-community`
- use helm to install the kube-prometheus-stack
`helm install kube-prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring -f values.yaml` 


## Poke around prom, alertmanager grafana and alertmanager
Prometheus and Alertmanager Web Panel
`kubectl port-forward svc/kube-prometheus-stack-prometheus 9090:9090 -n monitoring` 

`kubectl port-forward alertmanager-kube-prometheus-stack-alertmanager-0 9093 -n monitoring`

Grafana Web Panel 
`kubectl port-forward svc/kube-prometheus-stack-grafana 3000:80 -n monitoring`

```
user: admin
pass: prom-operator
```

## Generate Slack Webhook
* Go to api.slack.com 
* Create an app 
* Turn on the 'Enable Incoming Webhooks' option 
* Generate a Webhook URL 
* Test with a POST request from cURL 

## Setup AlertManager and Alert Rules 

### Configure AlertManager 

`helm upgrade --reuse-values -f alertmanager-config.yaml kube-prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring`


### Setup an alert using a default alert from AlertManager
`helm upgrade --reuse-values -f alert-rules.yaml kube-prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring`

## Thank You!
# Stay Connected !!

https://www.youtube.com/channel/UCNwP7KEElaJ7cdDTLP-KbBg

https://www.linkedin.com/in/azizul-maqsud/

https://azizulmaqsud-1684501031000.hashnode.dev/

https://medium.com/@azizulmaqsud

https://twitter.com/Sohail2me

https://github.com/azizulmaqsud


<a href="https://www.buymeacoffee.com/azizulmaqsud"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=scaleupsaas&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>

