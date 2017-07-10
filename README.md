# ELK stack for OpenShift on AWS

## Running OpenShift on AWS
Our OpenShift Origin instance runs on CentOS 7, configured using the following walkthrough: https://www.clouda.ca/blog/general/openshift-on-centos-7-quick-installation/

## Setup
```
# Kibana
sudo oc new-app https://github.com/amida-tech/elk-openshift-aws --context-dir=kibana --name=kibana
sudo oc expose service kibana

# Elasticsearch
sudo oc new-app https://github.com/amida-tech/elk-openshift-aws --context-dir=elasticsearch --name=elasticsearch

# Logstash
sudo oc new-app https://github.com/amida-tech/elk-openshift-aws --context-dir=logstash --name=logstash
```

## Persisting data
If you want to guarantee that your Elasticsearch data is persisted across any cluster changes,
create a persistent volume claim from the OpenShift console. Then, mount it at `/usr/share/elasticsearch/data` within
the Elasticsearch deployment configuration.
