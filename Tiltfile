def create_namespace(name):
    k8s_yaml(blob("""apiVersion: v1
kind: Namespace
metadata:
  name: %s
""" % name))

create_namespace("mongodb-test")

k8s_yaml(helm("charts/community-operator", name = "mongodb-test", namespace = "mongodb-test", values = "values.yaml"))

objects = read_yaml_stream("mongodb.yaml")
for o in objects:
    o["metadata"]["namespace"] = "mongodb-test"
k8s_yaml(encode_yaml_stream(objects))

k8s_resource(
    objects = ["mongodb", "mongodb-password"],
    new_name = "mongodb",
)
