def create_namespace(name):
    k8s_yaml(blob("""apiVersion: v1
kind: Namespace
metadata:
  name: %s
""" % name))

name = "mongodb-test"

create_namespace(name)

create_namespace("monitoring")

k8s_yaml(helm("charts/mongodb-sharded", name, namespace = name, values = "values.yaml"))
