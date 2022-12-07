```sh
k get secret mongodb-test-mongodb-sharded -nmongodb-test -ojsonpath={.data.mongodb-root-password} | base64 -d

k run test --image=mongo -it --rm -- sh

mongosh --host mongodb-test-mongodb-sharded.mongodb-test -u root -p [root password]
```

# Reference
* https://www.mongodb.com/docs/manual/tutorial/convert-replica-set-to-replicated-shard-cluster/
* https://www.mongodb.com/docs/manual/tutorial/modify-chunk-size-in-sharded-cluster/
