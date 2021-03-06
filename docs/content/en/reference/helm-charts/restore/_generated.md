

![Version: 0.27.1](https://img.shields.io/badge/Version-0.27.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| K8ssandra Team | k8ssandra-developers@googlegroups.com | https://github.com/k8ssandra |

## Source Code

* <https://github.com/k8ssandra/k8ssandra>
* <https://github.com/k8ssandra/k8ssandra/tree/main/charts/restore>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| name | string | `"restore"` | Name of the CassandraRestore custom resource |
| backup.name | string | `"backup"` | Name of the CassandraBackup custom resource to be restored from |
| cassandraDatacenter.name | string | `"dc1"` | Name of the CassandraDatacenter where the CassandraBackup will be restored |
| inPlace | bool | `true` | In-place restore will restore the backup to the source cluster. |
| shutdown | bool | `true` | When true will shutdown the entire Cassandra cluster. The underlying StatefulSets are scaled down to zero. Persistent volumes remain intact. If the backup includes schema changes like dropping a table, then must be set to true; otherwise, the changes will be lost via gossip from nodes that have not yet been restored. It is recommended in general to shutdown the cluster prior to a restore to avoid data inconsistencies and/or data loss that could happen with clients writing to the cluster while the restore operation is in progress. When set the cluster is shutdown, and the restore operations happen in parallel across all Cassandra pods. If `shutdown` is `false` the restore operation is done via a rolling restart where the restore operation runs on each pod serially. |
